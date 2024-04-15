## Table of Contents

- [Maven Project Creation](#Maven%20Project%20Creation)
- [Maven Configuration](#Maven%20Configuration)
	- [Disabling pluginManagement](#Disabling%20pluginManagement)
	- [Adding Checkstyle Plugin to Maven](#Adding%20Checkstyle%20Plugin%20to%20Maven)
	- [Maven Checkstyle Plugin Configuration](#Maven%20Checkstyle%20Plugin%20Configuration)
	- [Running Maven Checkstyle](#Running%20Maven%20Checkstyle)
- [Creating a branch](#Creating%20a%20branch)
- [Merge Configuration](#Merge%20Configuration)
- [Merging](#Merging)
- [Pushing to the Remote](#Pushing%20to%20the%20Remote)
## Maven Project Creation

Open a new **Visual Studio Code** window.
 ![[Screenshot 2024-04-14 at 12.35.22.png]]
 Press `cmd+shift+p` on **macOS** or `ctrl+shift+p` on **Windows**. Type `maven`, and click on **Maven: New Project...** option.
![[Screenshot 2024-04-14 at 12.35.29.png]]
Choose `maven-archetype-quickstart` option for quick setup of default project requirements.
![[Screenshot 2024-04-14 at 12.35.35.png]]
Choose `1.4` for the version.
![[Screenshot 2024-04-14 at 12.35.39.png]]
Write `edu.yasar.se3314` as group id of your project.
![[Screenshot 2024-04-14 at 12.35.46.png]]
Type corresponding week. In this tutorial it is `week9`.
![[Screenshot 2024-04-14 at 12.36.35.png]]
You will be prompted to navigate to master directory that project folder going to be created. Choose your repository of weeks created earlier weeks.
![[Screenshot 2024-04-14 at 12.37.03.png]]
When project creation done, you will be prompted to open new project.
![[Screenshot 2024-04-14 at 12.37.23.png]]
If completed successfully, new project windows will look like the image below.
![[Screenshot 2024-04-14 at 12.37.37.png]]
## Maven Configuration

### Disabling pluginManagement

Navigate to `pom.xml` file. Comment out `<pluginManagement>` opening tag.
![[Screenshot 2024-04-14 at 12.38.28.png]]
Then, scroll down the page and comment out `</pluginManagement>` closing tag.
![[Screenshot 2024-04-14 at 12.38.32.png]]
The `pluginManagement` tags are there by default to prevent change of versions just in case. Then click **Yes** for synchronize project configuration.
![[Screenshot 2024-04-14 at 12.38.38.png]]
### Adding Checkstyle Plugin to Maven

Scroll bottom of the `plugins` tag and paste following XML snippet.

```XML
<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-checkstyle-plugin</artifactId>
	<version>3.1.1</version>
	<dependencies>
	    <dependency>
		    <groupId>com.puppycrawl.tools</groupId>
		    <artifactId>checkstyle</artifactId>
		    <version>8.44</version>
		</dependency>
	</dependencies>
	<executions>
	    <execution>
			<id>verify</id>
		    <phase>verify</phase>
		    <configuration>
			    <configLocation>checkstyle.xml</configLocation>
		        <!-- other configurations -->
		    </configuration>
		    <goals>
		        <goal>check</goal>
		    </goals>
		</execution>
	</executions>
</plugin>
```

It should look like the image below.
![[Screenshot 2024-04-14 at 12.39.59.png]]
### Maven Checkstyle Plugin Configuration

Open file explorer and create a new XML file called `checkstyle.xml`.
![[Screenshot 2024-04-14 at 12.40.31.png]]
Paste following check configuration to `checkstyle.xml` file.

```xml
<?xml version="1.0"?>

<!DOCTYPE module PUBLIC "-//Checkstyle//DTD Checkstyle Configuration 1.3//EN" "https://checkstyle.org/dtds/configuration_1_3.dtd">

<module name="Checker">
  <property name="severity" value="error" />
  <module name="TreeWalker">
    <!-- JavaDoc Checks -->
    <module name="InvalidJavadocPosition" />
    <module name="JavadocContentLocation" />
    <module name="JavadocMethod"> </module>
    <module name="JavadocMissingLeadingAsterisk" />
    <module name="JavadocMissingWhitespaceAfterAsterisk" />
    <!-- <module name="JavadocParagraph"/> -->
    <module name="JavadocStyle" />
    <!-- <module name="JavadocTagContinuationIndentation">
		<property name="offset" value="2"/>
	</module> -->
    <module name="JavadocType" />
    <module name="JavadocVariable" />
    <module name="MissingJavadocMethod">
      <property name="scope" value="private" />
      <property name="tokens" value="METHOD_DEF" />
    </module>
    <module name="MissingJavadocType">
      <property name="scope" value="public" />
    </module>
    <module name="NonEmptyAtclauseDescription" />
    <module name="RequireEmptyLineBeforeBlockTagGroup" />

    <!-- Working Classes -->

    <!-- Good Encapsulation -->
    <module name="VisibilityModifier" />
    <module name="HideUtilityClassConstructor" />
    <module name="DesignForExtension" />

    <!-- Good Abstraction -->
    <module name="AbstractClassName" />
    <module name="ClassDataAbstractionCoupling" />
    <module name="InterfaceIsType" />

    <!-- Good Inheritance -->
    <module name="ClassFanOutComplexity">
      <property name="max" value="2" />
      <!-- <property name="excludedClasses" value="BuildComputerApp" /> -->
    </module>
    <module name="AvoidStarImport">
      <!-- <property name="excludes" value="java.io,java.net,java.lang.Math" /> -->
    </module>
    <module name="MissingOverride" />

    <!-- Member Functions -->
    <module name="MissingCtor"> </module>
    <module name="OverloadMethodsDeclarationOrder" />
    <module name="MethodCount">
      <property name="maxPublic" value="10" />
      <property name="maxPrivate" value="10" />
      <property name="maxTotal" value="40" />
    </module>

    <!-- Class Internals -->
    <module name="InnerTypeLast" />
    <module name="HideUtilityClassConstructor" />

    <!-- High Quality Routines -->

    <!-- Naming and Definition -->

    <module name="MethodName" />
    <!-- <module name="MethodLength">
		<property name="max" value="4" />
	</module> -->
    <module name="MethodParamPad" />
    <module name="MethodTypeParameterName" />
    <module name="FinalParameters">
      <!-- <property name="tokens" value="CTOR_DEF"/> -->
      <!-- <property name="ignorePrimitiveTypes" value="true"/> -->
    </module>
    <module name="ParameterName">
      <!-- <property name="format" value="^[a-z][_a-zA-Z0-9]+$"/> -->
    </module>
    <module name="ParameterNumber">
      <property name="max" value="10" />
      <property name="tokens" value="METHOD_DEF" />
      <!-- <property name="tokens" value="CTOR_DEF"/> -->
      <!-- <property name="ignoreOverriddenMethods" value="true"/> -->
      <!-- <property name="ignoreAnnotatedBy" value="JsonCreator"/> -->
    </module>

    <!-- Internals -->
    <module name="EmptyLineSeparator">
      <property name="tokens" value="VARIABLE_DEF, METHOD_DEF" />
	      <!-- <property name="allowNoEmptyLineBetweenFields" value="true"/> -->
	      <!-- <property name="allowMultipleEmptyLines" value="false"/> -->
	      <!-- <property name="allowMultipleEmptyLinesInsideClassMembers" value="false"/> -->
    </module>
    <module name="RequireThis">
      <property name="checkMethods" value="false" />
      <property name="checkFields" value="false" />
      <property name="validateOnlyOverlapping" value="false" />
    </module>
    <module name="ReturnCount">
      <property name="maxForVoid" value="0" />
      <property name="tokens" value="CTOR_DEF" />
    </module>
    <module name="ReturnCount">
      <property name="max" value="1" />
      <property name="tokens" value="LAMBDA" />
    </module>
    <module name="ReturnCount">
      <property name="max" value="2" />
      <property name="tokens" value="METHOD_DEF" />
    </module>
    <module name="JavaNCSS">
      <property name="methodMaximum" value="40" />
      <!-- <property name="fileMaximum" value="200"/> -->
    </module>
    
    <!-- Java Specific Checks -->
    <module name="CovariantEquals" />
    <module name="SuperClone" />
    <module name="SuperFinalize" />
  </module>
</module>
```

It should look like the given image below.
![[Screenshot 2024-04-14 at 12.41.26.png]]
### Running Maven Checkstyle

Open a terminal window.
![[Screenshot 2024-04-14 at 12.41.46.png]]
Type `mvn verify`.
![[Screenshot 2024-04-14 at 12.41.51.png]]
This will build, test and run checkstyle plugin. When it's done, one can view checkstyle violations.
![[Screenshot 2024-04-14 at 12.42.36.png]]
## Creating a branch

## Merge Configuration

Open **SourceTree** settings and navigate to the tab **Git**. Check **Do not fast-forward when merging, always create commit**. This will create a merge commit instead of directly merging source branch to target branch.
![[Screenshot 2024-04-14 at 12.06.12.png]]
## Merging

Navigate to **Workspace > History**. Switch to the branch `main`.
![[Screenshot 2024-04-14 at 12.49.22.png]]
Right click on the branch you would like to merge. In this case, it is `week9`.
![[Screenshot 2024-04-14 at 12.52.11.png]]
Click **Merge** on the context menu.
![[Screenshot 2024-04-14 at 12.52.18.png]]
A pop-up window will appear. Check both options.

>[!INFO] The option **Commit merged changes immediately** makes the merge commit automatically. If you don't check it then **SourceTree** will write a merge commit message have changes staged but will not commit automatically. This may be helpful for the case that the developer might want to add some additional details regarding the merge.

![[Screenshot 2024-04-14 at 12.52.23.png]]
## Pushing to the Remote

Click on **Fetch** before pushing anything to a remote repository. 

>[!INFO] **Fetch** will let you check that if changes happened while you are coding. If there are changes then you may need to pull those and run a merge.

![[Screenshot 2024-04-14 at 12.52.28.png]]
Click **OK**.
![[Screenshot 2024-04-14 at 12.52.41.png]]
Assuming that there are no changes on the remote repository. Continue by clicking **Push**. Select the branches you would like to push. In this case, both `main` and `week9`. Then click **OK**.
![[Screenshot 2024-04-14 at 12.52.58.png]]



















