# packages
A central repository for holding all uk.co.lukestevens Packages

## Setting up a project to publish to package repository
- Copy the `.github` and `.m2` directories to your project
- Add `distributionManagement` details to `pom.xml` (see below)

```xml
<distributionManagement>
  <repository>
    <id>github</id>
    <name>GitHub lukecmstevens Apache Maven Packages</name>
    <url>https://maven.pkg.github.com/lukecmstevens/packages</url>
  </repository>
</distributionManagement>
```

- Add `GH_ACCESS_TOKEN` to repository secrets
- Push only `SNAPSHOT` versions to develop, and final versions to master

## Setting up local maven settings to install from package repository
- If it doesn't exist, create a new `~/.m2/settings.xml` file using the example in this repository
- If it does exist, make sure the following is added under the `<repositories>` node:

```xml
<repository>
  <id>github</id>
  <name>GitHub lukecmstevens Apache Maven Packages</name>
  <url>https://maven.pkg.github.com/lukecmstevens/packages</url>
  <snapshots><enabled>true</enabled></snapshots>
</repository>
```

- and this is under the `<servers>` node (where `GH_ACCESS_TOKEN` is an authenticated access token):

```xml
<server>
  <id>github</id>
  <username>lukecmstevens</username>
  <password>GH_ACCESS_TOKEN</password>
</server>
```
