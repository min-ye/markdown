### Installation
* Download gradle from https://gradle.org/
* Unzip to file, the folder is gradle-2.13, copy the folder to C:\Tools;
* Set the evnironment variable GRADLE_HOME as C:\Tools\gradle-2.13;
* Add the %GRADLE_HOME%/bin to the PATH;
* Run 'gradle -v' to check;
export GRADLE_HOME=~/Tools/gradle/2.13
export PATH=$GRADLE_HOME/bin
Install BuildShip on Eclipse marketplace as the gradle plugin;
Show the view of Gradle Tasks and Gradle Executions;
Window -> Show View -> Other …;
Create a gradle project;
Right click build gradle and select Gradle -> Refresh Gradle Project to download the dependencies jar;
Right click build on Gradle Tasks, select Run Gradle Tasks to build the project;
Right click the other tasks on Gradle Tasks view to execute the task;
Add the following script on the build.gradle to make the jar can be execute;
jar {
    manifest {
        attributes 'Main-Class': 'com.lia.spring.c01.KnightMain'
    }
}
Add the following task to make the jar contains the dependencies jar;
task fatJar(type: Jar) {
    manifest {
        attributes 'Main-Class': 'com.lia.spring.c01.KnightMain'
    }
    baseName = project.name + '-all'
    from { configurations.compile.collect { it.isDirectory() ? it : zipTree(it) } }
    with jar
}
Run gradle fatJar to generate the jar package; 