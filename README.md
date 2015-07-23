# JVM: Java Version Manager

JVM is a tool for managing JVM versions on Mac OS X

## Install

Put the (self-contained) [jvm script](https://raw.githubusercontent.com/jkutner/jvm/master/jvm)
somewhere on your path, for example:

```
$ curl -s https://raw.githubusercontent.com/jkutner/jvm/master/jvm > ~/bin/jvm \
  && chmod 0755 ~/bin/jvm
```

## Sample Usage

```sh-session
# You need to run these commands first to set things up. I put these lines in my .profile
$ export JAVA_HOME=~/local/java_home
$ jvm fix

$ jvm list
=== JDK Versions
7 => jdk1.7.0_80.jdk
  => jdk1.8.0_45.jdk
8 => jdk1.8.0_51.jdk
9 => jdk1.9.0.jdk

$ jvm use 8
Using jdk1.8.0_51.jdk...
java version "1.8.0_51"
Java(TM) SE Runtime Environment (build 1.8.0_51-b16)
Java HotSpot(TM) 64-Bit Server VM (build 25.51-b03, mixed mode)

$ jvm use jdk1.8.0_45.jdk
Using jdk1.8.0_45.jdk...
java version "1.8.0_45"
Java(TM) SE Runtime Environment (build 1.8.0_45-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.45-b02, mixed mode)

$ jvm help
Usage: jvm [command] [args]

Commands:
  list          - list the available JDKs
  use [version] - use a particular JDK version
  fix           - forceable reset to default
```

## How it works

This tool creates a symlink, like `~/local/java_home`, which is set to `$JAVA_HOME`.
The tool then switches out this symlink as needed.
