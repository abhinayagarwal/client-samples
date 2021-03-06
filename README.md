# Gluon Client Samples

Java and JavaFX samples to run with GraalVM and the Gluon Client plugins for [Maven](https://github.com/gluonhq/client-maven-plugin/).

For now only Linux, Mac OS X, iOS and Android platforms are supported. 

## Build and run the samples

### Requirements

#### Mac OS X and iOS

* Download this version of Graal VM: https://download2.gluonhq.com/substrate/graalvm/graalvm-svm-darwin-20.1.0-ea+26.zip and unpack it like you would any other JDK. (e.g. in `/opt`)

* Configure the runtime environment. Set `GRAALVM_HOME` environment variable to the GraalVM installation directory.

For example:

    export GRAALVM_HOME=/opt/graalvm-svm-darwin-20.1.0-ea+26

* Set `JAVA_HOME` to point to the GraalVM installation directory

For example:

    export JAVA_HOME=$GRAALVM_HOME

#### Linux and Android

* Download this version of Graal VM: https://download2.gluonhq.com/substrate/graalvm/graalvm-svm-linux-20.1.0-ea+26.zip and unpack it like you would any other JDK. (e.g. in `/opt`)

* Configure the runtime environment. Set `GRAALVM_HOME` environment variable to the GraalVM installation directory.

For example:

    export GRAALVM_HOME=/opt/graalvm-svm-linux-20.1.0-ea+26

* Set `JAVA_HOME` to point to the GraalVM installation directory

For example:

    export JAVA_HOME=$GRAALVM_HOME

### Build using Maven

#### HelloWorld, HelloFX, HelloFXML and HelloGluon samples

The following goals apply to Linux and Mac OS X.

To build the native image:

    mvn clean client:build

To run the native image:

    mvn client:run

or simply run the native executable found in `target/client`.

## Build and run the samples on iOS

### Additional requirements

* iOS can be built only on Mac OS X

* Install `Homebrew`, if you haven't already. Please refer to https://brew.sh/ for more information.

* Install `libusbmuxd`

Using `brew`:

    brew install --HEAD libusbmuxd

* Install `libimobiledevice`

Using `brew`:

    brew install --HEAD libimobiledevice

### Build using Maven

#### HelloWorld, HelloFX, HelloFXML and HelloGluon samples


* Set the target to `ios` (for iOS devices) in the `pom.xml`:

```
<artifactId>client-maven-plugin</artifactId>
<configuration>
    <target>ios</target>
    <mainClass>${mainClassName}</mainClass>
</configuration>
```

* Build the native image:

```
mvn clean client:build
```

* Run the app on the connected iOS device:

```
mvn client:run
```

* Package and create an IPA file to submit to TestFlight or to the App Store:

```
mvn client:package
```

**Note**: Since all java bytecode is translated to native code, the compilation step can take a long time, and it requires a fair amount of memory.

**Note**: In order to deploy apps to an iOS device, you need a valid iOS provisioning profile, as explained in the [documentation](https://docs.gluonhq.com/client/#_ios_deployment).

## Build and run the samples on Android

### Additional requirements

* Android can be built only on Linux OS

The client plugin will download the Android SDK and install the required packages. Alternatively, you can define a custom location to the Android SDK by setting the `ANDROID_SDK` environment variable, making sure that you have installed all the packages from the following list:

* platforms;android-27
* platform-tools
* build-tools;27.0.3
* ndk-bundle
* extras;android;m2repository
* extras;google;m2repository

### Build using Maven

#### HelloWorld, HelloFX, HelloFXML and HelloGluon samples

* Set the target to `android` (for android devices) in `pom.xml`:

```
<artifactId>client-maven-plugin</artifactId>
<configuration>
    <target>android</target>
    <mainClass>${mainClassName}</mainClass>
</configuration>
```

* Build the native image:

```
mvn clean client:build
```

* Package and create an APK file:

```
mvn client:package
```

* Install the APK file on a connected Android device:

```
mvn client:install
```

* Run the installed app on the connected Android device:

```
mvn client:run
```

**Note**: Since all java bytecode is translated to native code, the compilation step can take a long time, and it requires a fair amount of memory.

## Issues and Contributions ##

Issues can be reported to the [Issue tracker](https://github.com/gluonhq/client-samples/issues)

Contributions can be submitted via [Pull requests](https://github.com/gluonhq/client-samples/pulls), 
providing you have signed the [Gluon Individual Contributor License Agreement (CLA)](https://docs.google.com/forms/d/16aoFTmzs8lZTfiyrEm8YgMqMYaGQl0J8wA0VJE2LCCY) 
(See [What is a CLA and why do I care](https://www.clahub.com/pages/why_cla) in case of doubt).
