# Apache-Nifi
Apache Nifi for Data Engineering

# NiFiTemplates
A collection of templates for use with Apache NiFi and an excel file which indicates what processors/controller services are in each template. This collection is meant to be a place for users to come to see how processors are configured or potentially used. As well as for developers to have easy access to templates to test their changes with.

The counts along the top of the excel file indicate how many templates currently use that processor.

https://nifi.apache.org/ is an easy to use, powerful, and reliable system to process and distribute data.

# Features

Apache NiFi was made for dataflow. It supports highly configurable directed graphs of data routing, transformation, and system mediation logic. Some of its key features include:

    Web-based user interface
        Seamless experience for design, control, and monitoring
        Multi-tenant user experience
    Highly configurable
        Loss tolerant vs guaranteed delivery
        Low latency vs high throughput
        Dynamic prioritization
        Flows can be modified at runtime
        Back pressure
        Scales up to leverage full machine capability
        Scales out with zero-master clustering model
    Data Provenance
        Track dataflow from beginning to end
    Designed for extension
        Build your own processors and more
        Enables rapid development and effective testing
    Secure
        SSL, SSH, HTTPS, encrypted content, etc...
        Pluggable fine-grained role-based authentication/authorization
        Multiple teams can manage and share specific portions of the flow

# Requirements

    JDK 1.8 (ongoing work to enable NiFi to run on Java 9/10/11; see NIFI-5174)
    Apache Maven 3.1.1 or newer
    Git Client (used during build process by 'bower' plugin)

Getting Started

    Read through the quickstart guide for development. It will include information on getting a local copy of the source, give pointers on issue tracking, and provide some warnings about common problems with development environments.
    For a more comprehensive guide to development and information about contributing to the project read through the NiFi Developer's Guide.

To build:

    Execute mvn clean install or for parallel build execute mvn -T 2.0C clean install. On a modest development laptop that is a couple of years old, the latter build takes a bit under ten minutes. After a large amount of output you should eventually see a success message.

      laptop:nifi myuser$ mvn -T 2.0C clean install
      [INFO] Scanning for projects...
      [INFO] Inspecting build with total of 115 modules...
          ...tens of thousands of lines elided...
      [INFO] ------------------------------------------------------------------------
      [INFO] BUILD SUCCESS
      [INFO] ------------------------------------------------------------------------
      [INFO] Total time: 09:24 min (Wall Clock)
      [INFO] Finished at: 2015-04-30T00:30:36-05:00
      [INFO] Final Memory: 173M/1359M
      [INFO] ------------------------------------------------------------------------

    Execute mvn clean install -DskipTests to compile tests, but skip running them.

To deploy:

    Change directory to 'nifi-assembly'. In the target directory, there should be a build of nifi.

      laptop:nifi myuser$ cd nifi-assembly
      laptop:nifi-assembly myuser$ ls -lhd target/nifi*
      drwxr-xr-x  3 myuser  mygroup   102B Apr 30 00:29 target/nifi-1.0.0-SNAPSHOT-bin
      -rw-r--r--  1 myuser  mygroup   144M Apr 30 00:30 target/nifi-1.0.0-SNAPSHOT-bin.tar.gz
      -rw-r--r--  1 myuser  mygroup   144M Apr 30 00:30 target/nifi-1.0.0-SNAPSHOT-bin.zip

    For testing ongoing development you could use the already unpacked build present in the directory named "nifi-version-bin", where version is the current project version. To deploy in another location make use of either the tarball or zipfile and unpack them wherever you like. The distribution will be within a common parent directory named for the version.

      laptop:nifi-assembly myuser$ mkdir ~/example-nifi-deploy
      laptop:nifi-assembly myuser$ tar xzf target/nifi-*-bin.tar.gz -C ~/example-nifi-deploy
      laptop:nifi-assembly myuser$ ls -lh ~/example-nifi-deploy/
      total 0
      drwxr-xr-x  10 myuser  mygroup   340B Apr 30 01:06 nifi-1.0.0-SNAPSHOT

To run NiFi:

    Change directory to the location where you installed NiFi and run it.

      laptop:~ myuser$ cd ~/example-nifi-deploy/nifi-*
      laptop:nifi-1.0.0-SNAPSHOT myuser$ ./bin/nifi.sh start

    Direct your browser to http://localhost:8080/nifi/ and you should see a screen like this screenshot: 
    https://raw.githubusercontent.com/apache/nifi/master/nifi-docs/src/main/asciidoc/images/nifi_first_launch_screenshot.png
