## Use Robotium with Maven ##

This is what you need:
  * Set up your project(s) as usual for Maven, see [android-maven-plugin](http://code.google.com/p/maven-android-plugin/).
  * Add a dependency to Robotium in your **test** project:
```
    <dependencies>
        <dependency>
            <groupId>com.jayway.android.robotium</groupId>
            <artifactId>robotium-solo</artifactId>
            <version>5.0.1</version>
        </dependency>

        ...

    </dependencies>

```

**NB: For the version number, enter the version number of the latest release!**

### Help testing a specific SNAPSHOT version ###

If you have been instructed to help test a specific SNAPSHOT version of Robotium, please add this repository to your pom:

```
        <repository>
            <id>oss.sonatype.org-jayway-with-staging</id>
            <url>http://oss.sonatype.org/content/groups/jayway-with-staging/</url>
            <snapshots><enabled>true</enabled></snapshots>
        </repository>
```

Then set the version number for robotium-solo to the desired version number, for example:

```
        <version>5.0.2-SNAPSHOT</version>
```