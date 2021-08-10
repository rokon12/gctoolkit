# Microsoft GCToolKit

GCToolkit is a set of libraries for analyzing Java garbage collection (GC) log files. The toolkit parses GC log files into discrete events and provides an API for aggregating data from those events. This allows the user to create arbitrary and complex analyses of the state of managed memory in the Java Virtual Machine (JVM) represented by the garbage collection log.

For more detail you can read our [Launch Blog Post](https://devblogs.microsoft.com/java/introducing-microsoft-gctoolkit/).

[![GCToolKit build with Maven](https://github.com/microsoft/gctoolkit/actions/workflows/maven.yml/badge.svg)](https://github.com/microsoft/gctoolkit/actions/workflows/maven.yml)

---

## Introduction

Managed memory in the Java Virtual Machine (JVM) is comprised of 3 main pieces:

1. Memory buffers known as Java heap
1. Allocators which perform the work of getting data into Java heap
1. Garbage Collection (GC).

While GC is responsible for recovering memory in Java heap that is no longer in use, the term is often used as a euphemism for memory management. The phrasing of _Tuning GC_ or _tuning the collector_ are often used with the understanding that it refers to tuning the JVM’s memory management subsystem. The best source of telemetry data for tuning GC comes from GC Logs and GCToolKit has been helpful in making this task easier by providing parsers, models and an API to build analytics with. You can run the Maven project [HeapOccupancyAfterCollectionSummary sample](./sample/pom.xml) as an example of this.

## Prerequisite for Building GCTooKit

The gctoolkit build relies on test data which is archived in [GitHub Packages](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-apache-maven-registry). This requires you to [authenticate to GitHub packages with a personal access token (PAT)](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-apache-maven-registry#authenticating-with-a-personal-access-token) to build and test.

If your organization uses Single Sign-On (SSO), also follow the directions under [Authorizing a personal access token for use with SAML single sign-on](https://docs.github.com/en/github/authenticating-to-github/authenticating-with-saml-single-sign-on/authorizing-a-personal-access-token-for-use-with-saml-single-sign-on).

You must also add github as a server in your `~/.m2/settings.xml` file. Replace USERNAME with your GitHub user name and TOKEN with your PAT.

```xml
    <server>
      <id>github</id>
      <username>USERNAME</username>
      <password>TOKEN</password>
    </server>
```

---

## Getting Started

### Maven Coordinates

TODO Add some context as to why we need this and where it should go.

```xml
<repository>
    <id>github</id>
    <name>GCToolKit packages</name>
    <url>https://maven.pkg.github.com/microsoft/*</url>
</repository>
```

```xml
<dependency>
    <groupId>com.microsoft.gctoolkit</groupId>
    <artifactId>api</artifactId>
    <version>2.0.1-SNAPSHOT</version>
</dependency>

<dependency>
    <groupId>com.microsoft.gctoolkit</groupId>
    <artifactId>parser</artifactId>
    <version>2.0.1-SNAPSHOT</version>
</dependency>

<dependency>
    <groupId>com.microsoft.gctoolkit</groupId>
    <artifactId>vertx</artifactId>
    <version>2.0.1-SNAPSHOT</version>
</dependency>

```

### Example

TODO Shell script needs to be added.

```shell
cd sample
./sample.sh
```

## Build and Test

The build is vanilla Maven.

* `mvn clean` - remove build artifacts
* `mvn compile` - compile the source code
* `mvn test` - run unit tests (this project uses TestNG)
* `mvn package` - build the .jar file

## Contributing

See [CONTRIBUTING.md] for full details.

## License

Microsoft GCToolKit is licensed under the [MIT](https://github.com/microsoft/gctoolkit/blob/master/LICENSE) license.
