### How do I get started with Robotium? ###

Download the [Robotium jar](http://dl.bintray.com/robotium/generic/robotium-solo-5.3.1.jar) and add it to your test project's build path. For further instructions go to our [getting started page.](http://code.google.com/p/robotium/wiki/Getting_Started) There you will find a link to the tutorials page and an example test project that can be downloaded and run through Eclipse.


### Which versions of Android does Robotium support? ###

Robotium officially supports Android API level 8 and up.

### Does Robotium support testing on real devices? ###

Yes it does. One just needs to connect the device to the computer and execute the tests as usual. There can be issues with some vendor customizations of Android, but many times it is possible to get around the incompatibilities by using other Robotium methods.

### Which features does Robotium support? ###

You can access the [Javadoc online](http://robotium.googlecode.com/svn/doc/index.html)  to see a full list of Robotium features. You can also download the [Javadoc](http://dl.bintray.com/robotium/generic/robotium-solo-5.3.1-javadoc.jar). The Javadoc is a jar file that builds on the zip file format. If you do not know how to extract its content you can rename it to .zip instead and extract it with your favourite zip extraction tool.


### Is it possible to write a test case that spans over 2 applications? ###

No, that is not possible. In the AndroidManifest.xml you state which target application you want to test. An example of what it can look like:

```
<instrumentation android:targetPackage="com.example.android.notepad" android:name="android.test.InstrumentationTestRunner" />
```

That means that the test project is locked to the `targetPackage`. Going outside of that target package is not allowed by the Android platform. Therefore you will need 2 test projects, one for each application.


### Can I use Robotium if I only have the apk file? ###

Yes you can. You do not need to have the source code. More information is [found here.](http://code.google.com/p/robotium/wiki/RobotiumForAPKFiles)


### Can I use Robotium on pre-installed applications? ###

Yes you can if you have a rooted phone. More information is [found here.](http://code.google.com/p/robotium/wiki/RobotiumForPreInstalledApps)


### Can I use Robotium with hybrid (web) applications? ###

Yes you can. Since Robotium 4.0, applications with web content are supported.

### Can I take screenshots from inside of Robotium? ###

Yes you can. Use takeScreenshot() to save a screenshot in "/sdcard/Robotium-Screenshots/". Observe that this functionality requires write permission (android.permission.WRITE\_EXTERNAL\_STORAGE) in the AndroidManifest.xml of the application under test.


### How do I run Robotium tests from the command line? ###

By using this command:

```
adb shell am instrument -w com.android.foo/android.test.InstrumentationTestRunner
```

Where `com.android.foo` is the name of your test project's package. More on this can be [found here.](http://developer.android.com/reference/android/test/InstrumentationTestRunner.html)

### Why do text and button clicks get wrong? ###

If this problem happens on one of the supported versions then try to add this tag to the test project's AndroidManifest.xml

```
<uses-sdk android:targetSdkVersion="YOUR_VERSION" /> 
```

Where `YOUR_VERSION` is `6` for Android 2.0, `7` for Android 2.1 and `8` for Android 2.2.

If that does not solve the problem then try to add this tag to the AndroidManifest.xml of the application you want to test:

```
<supports-screens android:anyDensity="true"/> 
```

If neither of these solutions solve your problems then write an [issue report.](http://code.google.com/p/robotium/issues/list)

### Can I test with localised strings? ###
Yes you can. You can use `solo.getString(int id)` and in there pass in the resource id of the string that you want to use. Since Robotium 4.3, getString(String id) can be used when testing apps with no source code.

### How can I get code coverage for my Robotium tests? ###
You currently need to use ant (or for the perverse, the command line).

Because of security restrictions, you either need root access on the phone or to test in the emulator.

Here are the main steps
  * run `android update test-project -m [path to target application] -p [path to the test folder ` I'd recommend running this in the root folder of the tests, so ` -p . ` You need to run this before you can run the `ant coverage` command
  * the Robotium jar needs to be in the libs folder of your test project. e.g. on my windows machine when I'm in the root of my test project I ran the following command `copy \opensourceprojects\Robotium\downloads\robotium-solo-2.1.jar libs`
  * ant needs to access to the class files, and libraries of the target application (which assumes you have the source for that application and the ability to build it). For the gist see http://stackoverflow.com/questions/2472059/cant-build-and-run-an-android-test-project-created-using-ant-create-test-projec I have included the extract of my build.xml file below.
  * run `ant coverage`
  * if all's well the output from ant will tell you a coverage.html has been created in a folder called coverage. You can open that file in a web browser to see the coverage of your Robotium tests :)

Here's the extract of my custom build.xml file.
```
<!-- override "compile" target in platform android_rules.xml to include tested app's external libraries -->
<target name="compile" depends="-resource-src, -aidl"
            description="Compiles project's .java files into .class files">
    <!-- If android rules are used for a test project, its classpath should include
         tested project's location -->
    <condition property="extensible.classpath"
                       value="${tested.project.dir}/bin/classes" else=".">
        <isset property="tested.project.dir" />
    </condition>
    <javac encoding="ascii" target="1.5" debug="true" extdirs=""
            destdir="${out.classes.absolute.dir}"
            bootclasspathref="android.target.classpath"
            verbose="${verbose}" classpath="${extensible.classpath}">
        <src path="${source.absolute.dir}" />
        <src path="${gen.absolute.dir}" />
        <classpath>
            <fileset dir="${tested.project.dir}/libs" includes="*.jar" />
            <fileset dir="${tested.project.dir}/bin/classes" includes="*.class" />
            <fileset dir="${external.libs.absolute.dir}/libs" includes="*.jar" />
        </classpath>
    </javac>
</target>
```

You should copy and paste this into the current `build.xml` file for the tests. I'd also recommend creating or editing the `build.properties` files in the root folders of the tests and the target application with `emma.enabled=true`