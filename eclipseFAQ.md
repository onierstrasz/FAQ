# Eclipse-FAQ

## Q How do I enable assertions?
- `Eclipse > Preferences > Java > Installed JREs`
  Select `installed JRE`; Edit and enter `-ea` under `Default VM Arguments`

## Q How do I enable the Metrics view?
- `Properties>Metrics>Enable Metrics`

## Q How do I add a jar to the path of a project?
- Copy in the jar. Open project properties (right-click on the project folder icon). Select `Java Build Path>Add JARs`. Select the copied jar.

---
# OLDER FAQs to check ...

## Q How do I run a Makefile rule?
- `Window>Show View>Make targets`
  Double-click on the desired target

## Q I keep getting network connection errors. What's wrong?
- Try setting the http proxy
`Preferences > General > Network Connections`

## Q How do I change the location of the Workspace?
- Change `Preferences>General>Startup` to Prompt for Workspace

## Q Sharing a new project fails. What's wrong?
- Check the eclipse error log in `.metadata/.log`
If you have an old version of eclipse, grab the newest stable release from https://cvs.cvshome.org

## Q How do I change the Java editor font?  The preference GUI doesn't seem to work!
- `General>Appearance>Colors&Fonts>Java`
You must *close* the font widget before pressing the Apply button, else the new font will not take effect (!).

## Q How do I change the console font?
- A Go to `Appearance>Colors&Fonts>Debug>Console`

## Q How do I configure a project to use JUnit?
- `Project>Properties>JavaBuildPath>Libraries`
  and add the junit.jar in the eclipse plugins folder
  Add a Run configuration as a JUnit test
  Open a JUnit view and run the test.

## Q When I check out a tagged revision from cvs, it is missing the .classpath file and cannot build. How can I fix this?
- Manually add the .classpath and .project files to the tagged revision: cvs tag TAG .classpath .project

## Q I want to commit my changes, but cvs complains that the sticky tag for my files is not a branch. What do I do to fix this?
- Run `cvs update -A` to reset the sticky tags.  (Avoid modifying a project checked out by its tag -- you will need to define a new branch!)

## Q What do I specify in the MANIFEST file of a jar to enable Java 1.4 assertions?
- ???

## Q How do I get eclipse to work with Java 1.5?
- Install Java 5 from Apple.
	http://www.apple.com/downloads/macosx/apple/java2se50release1.html
- Make Java 5 the default
`/Applications/Utilities/Java/J2SE 5.0/Java Preferences.app`
See http://docs.info.apple.com/article.html?artnum=301073
- Install Eclipse 3.1 (www.eclipse.org)
- Set the `Eclipse>Preferences>Java>Compiler level` to 5.0
- Add the 1.5.0 JRE to `Eclipse>Preferences>Java>Installed JREs`
`/System/Library/Frameworks/JavaVM.framework/Versions/1.5.0/Home`
- Be sure to configure the compiler and JRE for each project appropriately!
See also:
http://vv.cs.byu.edu/~jones/blog/archives/2005/05/running_the_lat.html

## Q How do I install Java 1.7 and Eclipse Juno?
- download and install the JDK from oracle:

	http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html

- open the Java Control Panel from the System Preferences app and install any updates
- [optional] delete or rename any old eclipse in the Applications folder
- download the "Eclipse IDE for Java Developers", unzip and install in Applications

	http://www.eclipse.org/downloads/

- fire up eclipse

- Check if Java 1.7 is enabled
  - open Preferences>Java>Installed JREs
  - if you are lucky, it is installed and enabled (this worked only the second time I tried this)
  - if you are unlucky, add>Standard VM
  - find the path of the 1.7 VM, eg:

```
	cd /Library/Java/JavaVirtualMachines/jdk1.7.*.jdk/Contents/Home
	pwd
```

  - copy/paste the location to the field "JRE home"
  - "Finish"
  - enable the 1.7 VM (checkbox)

# Q How to manually install plugins?
- For example: http://scg.unibe.ch/wiki/projects/fontsizebuttons
- quit eclipse
- copy/paste the plugin directly into `/Applications/eclipse/Plugins`
- restart eclipse
- if it doesn't crash, Bob's your uncle

## Q How do I convince eclipse/MacOSX to run a jar using Java 5?
- ???

## Q I can't run cvs locally -- what's wrong?
- Make sure remote login is enabled.

## Q Why doesn't anything happen when I "Build Project"?
- Check if everything referred to in the .classpath really exists!

## Q. What is the shortcut for auto-completion?
-`.`

---

