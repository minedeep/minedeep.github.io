---
layout: post
type: post
title: "Install Hadoop and Spark on a remote Ubuntu server"
date: 2021-01-22
categories: technotes
comments: true
author: "Hailey Do"
tags: [big data, hadoop, spark, ssh]
description: |
    In this blog, I describe steps I took to install and run pseudo-distributed (single node deployment) Hadoop system and Spark on the same Ubuntu server
excerpt: |
    
---

Hadoop and Spark are both Apache open source project written on Java. Thus, before installing Hadoop and Spark, we need to install neccessary dependencies

## Installing JDK
Which version of JDK we should use to run a particular version of Hadoop and Spark. You may want to use SDKMAN to manage versions of JDK. How to install, configure, and run JDK with SDKMAN is beyond the scope of this blog. For the purpose of simplification, I will jsut install the latest version. Follow the below steps to install JDK on Ubuntu

### 1. Update apt by running ```s sudo apt-get update && sudo apt-get dist-upgrade ```
If you receive below errors, it's likely you are with an no-longer-supported Ubuntu version. You need to either upgrade Ubuntu or do the following trick: edit ``` /etc/apt/sources.list``` and change ``` archive.ubuntu.com ``` and ``` security.ubuntu.com ``` to ```old-releases.ubuntu.com. ```

You can do this with sed:```s sudo sed -i -re 's/([a-z]{2}\.)?archive.ubuntu.com|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list```

```s
Ign:4 http://us.archive.ubuntu.com/ubuntu eoan InRelease
Hit:5 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu eoan InRelease
Ign:6 http://us.archive.ubuntu.com/ubuntu eoan-updates InRelease
Ign:7 http://security.ubuntu.com/ubuntu eoan-security InRelease
Ign:8 http://us.archive.ubuntu.com/ubuntu eoan-backports InRelease
Err:9 http://security.ubuntu.com/ubuntu eoan-security Release
  404  Not Found [IP: 91.189.88.152 80]
Err:10 http://us.archive.ubuntu.com/ubuntu eoan Release
  404  Not Found [IP: 91.189.91.38 80]
Err:11 http://us.archive.ubuntu.com/ubuntu eoan-updates Release
  404  Not Found [IP: 91.189.91.38 80]
Hit:12 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu eoan InRelease
Err:13 http://us.archive.ubuntu.com/ubuntu eoan-backports Release
  404  Not Found [IP: 91.189.91.38 80]
``` 
### 2. Install JDK  ```s sudo apt install default-jdk -y ```
Check the success of java installation by executing ```s java -version ```. You should see somthing similar to the below
```s
openjdk version "11.0.7" 2020-04-14
OpenJDK Runtime Environment (build 11.0.7+10-post-Ubuntu-2ubuntu219.10)
OpenJDK 64-Bit Server VM (build 11.0.7+10-post-Ubuntu-2ubuntu219.10, mixed mode, sharing)
```
After installing JDK, you have to explicitly specify JAVA_HOME in the .bashrc file by running this command: 

```s echo "export JAVA_HOME=\$(readlink -f \$(which java) | sed 's:bin/java::')" >> ~/.bashrc
```
After that, run ``` echo $JAVA_HOME ``` for the path
### 3. Install Scala ```s sudo apt install scala git -y ```
### 4. Install Hadoop
Download Hadoop using wget. You can go to Apache homepage of Hadoop to get the download link for the latest version
```s
wget https://downloads.apache.org/hadoop/common/hadoop-3.2.1/hadoop-3.2.1.tar.gz
```
Extract the ```tar``` file and redirect the output to ```/opt```
```s
sudo tar -xvf hadoop-3.2.1.tar.gz -C /opt
sudo rm hadoop-3.2.1.tar.gz & cd /opt
```
Change the permisson so that it is owned by you (my ubuntu account is sopwil)
```s
sudo chown sopwil:sopwil -R hadoop-3.2.1
```
Define the HADOOP_HOME environment and add the Hadoop binaries to your PATH env and append them to ``` .bashrc``` file
```s
$ echo "export HADOOP_HOME=/opt/hadoop-3.2.1" >> ~/.bashrc
$ echo "export PATH=\$PATH:\$HADOOP_HOME/bin:\$HADOOP_HOME/sbin" >> ~/.bashrc
```
Finally source ```.bashrc``` file and now you should be able to check the version of the installed hadoop
```s
source ~/.bashrc
hadoop -version

Hadoop 3.2.1
Source code repository https://gitbox.apache.org/repos/asf/hadoop.git -r b3cbbb467e22ea829b3808f4b7b01d07e0bf3842
Compiled by rohithsharmaks on 2019-09-10T15:56Z
Compiled with protoc 2.5.0
From source with checksum 776eaf9eee9c0ffc370bcbc1888737
This command was run using /opt/hadoop/share/hadoop/common/hadoop-common-3.2.1.jar
```



