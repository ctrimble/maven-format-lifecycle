# Maven Format Lifecycle

This project provides a format lifecycle extension for maven builds, providing a convenient way to configure and execute
formatting plugins on your project.

## What is Provided?

This is an extremely simple extension.  It adds a new `format` lifecycle to your project, with the following phases:

- pre-format
- format
- post-format

You can then bind plugins to these phases and format your project using:

    mvn format

Out of the box, there are no plugins bound to this lifecycle.

## Adding this Extension

To add this extension to your project, add the following extensions block to your pom.xml:

```xml
<project>
  <build>
    <extensions>
      <extension>
        <groupId>com.xiantrimble.maven</groupId>
        <artifactId>maven-format-lifecycle</artifactId>
        <version>1.0.0</version>
      </extension>
    </extensions>
  </build>
</project>
```

## Binding Plugins

To bind plugin executions to this lifecycle, add an `<execution/>` block to the plugin:

```xml
<executions>
  <execution>
    <phase>format</phase>
    <goals>
      <goal>GOAL_TO_EXECUTE</goal>
    </goals>
  </execution>
</executions>
```

### Adding License Headers

The [com.mycila:license-maven-plugin](http://code.mycila.com/license-maven-plugin/) can be used to manage your license headers:

```xml
<plugin>
  <groupId>com.mycila</groupId>
  <artifactId>license-maven-plugin</artifactId>
  <version>2.6</version>
  <configuration>
    <!-- see project site for configuration details. -->
  </configuration>
  <executions>
    <execution>
      <phase>format</phase>
      <goals>
        <goal>format</goal>
      </goals>
    </execution>
  </executions>
</plugin>
```

### Formatting Source Code

The [com.googlecode.maven-java-formatter-plugin:maven-java-formatter-plugin](https://code.google.com/p/maven-java-formatter-plugin/) plugin can be
used to format your java source code using the eclipse formatter.

```xml
<plugin>
  <groupId>com.googlecode.maven-java-formatter-plugin</groupId>
  <artifactId>maven-java-formatter-plugin</artifactId>
  <version>0.4</version>
  <configuration>
    <!-- see project site for configuration details. -->
  </configuration>
  <executions>
    <execution>
      <phase>format</phase>
      <goals>
        <goal>format</goal>
      </goals>
    </execution>
  </executions>
</plugin>
```
