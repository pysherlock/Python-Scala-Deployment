# Python-Scala-Deployment

  Pre-requirement: Jep https://github.com/ninia/jep, called Jep - Java Embedded Python
  This library could help you emebed Python into Java&Scala。
  The reuslt is that we will be able to run our own cutomized Python ML algorithm within Scala/Java application, especially while working with Spark. We will have more flexibility rather than being limited by Spark ML.

## 1. Setting up environment
  The object of this step is setting up environment which could allow you to compile all your Python libraries in advance. Make sure the compile envrionment is same with the one on which you will deploy your project. This step is to ensure that you won't meet too many mistakes because of the conflicts between compile environment and running environment.

### 1.1 Install GCC & GLIBC
C-compile is necessary for Pyhon libraries. And it is the dangerous part in which you could meet conflicts. So you should make sure your compile envrionment has a gcc environment which is compatible with your running envrionment. 

Otherwise, you need to install a old/specific gcc version in your compile envrionment

#### How to install an old/specific gcc version (ubuntu)

Old version of gcc for new Ubuntu: 
  https://askubuntu.com/questions/39628/old-version-of-gcc-for-new-ubuntu;
  https://askubuntu.com/questions/789179/how-to-install-gcc-4-4-on-ubuntu-16-04

### 1.2 Compile your Python libraries with specific gcc 

For example, gcc 4.4

Specifiy your gcc version
