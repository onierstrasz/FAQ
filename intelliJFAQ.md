# IntelliJ FAQ

## Q How do I fix UnsupportedClassVersionError errors?

IJ complains that the class files have been compiled for a new Java.
Try to rebuild the project from the main menu: `Build > Rebuild project`

If that does not work, try to create the project afresh from existing sources.

## Q How to migrate tests from JU 4 to JU5?

A `Command+Shift+A` -- enter `migrate` -- `Return` -- `Select` and run `Migrate JU4 to JU5`

Delete JU4 configuration.
Check and edit all the migrate files. Eg change `@Before` to `@BeforeEach`
Update `imports` to
```
import org.junit.jupiter.api.*;
import static org.junit.jupiter.api.Assertions.*;
```

## Q How do I add JUnit 5 to a project?

I could only do it using a quick fix.

## Q How to run a main method?

`Command+Shift+f` to find main methods. Then run.

## Q How to run all tests?

Select the project folder and enter `Control-Shift-R`

## Q How to enable assertions?

- select `Run > Edit Configurations ...`
- select `Modify Options > Add VM options`
- enter `-ea` and save

## Q How to fix java.lang.NoClassDefFoundError: org/hamcrest/SelfDescribing error?

need to add hamcrest lib for unit test

`File -> Project Structure -> Libraries -> + -> Applications/IntelliJ IDEA.app/Contents/lib/hamcrest-core-1.3.jar`

## Q Why does IJ not find my source files?

Right -click on the file and it says `Java file outside of source root`.
Click on `Project settings > Modules`
Add the files. Select `import from Eclipse`.

## Q How do I fix java: JDK isn't specified for module ...

Go to Project settings and check the SDK.
Also check the configurations buitton for the class.

