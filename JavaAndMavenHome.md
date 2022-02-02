# How to set JAVA and MAVEN HOME on Windows

## JAVA_HOME
Download a version of the JAVA JDK:
- https://docs.aws.amazon.com/corretto/latest/corretto-11-ug/downloads-list.html
- https://openjdk.java.net/projects/jdk/11/

Press the windows icon > System Variables 

### JAVA_HOME
--> new > JAVA_HOME

> Enter a path similar to this one: `C:\Program Files (x86)\Amazon Corretto\jdk11.0.14_9`

### Path
--> Path > new
> `%JAVA_HOME%\bin`

## Maven_Home
Download maven. You can either use chocolatey: `choco install maven` 
the download is going to be under `c/ProgramData/chocolatey/lib/maven`.
Or simply donwload maven here: `https://maven.apache.org/download.cgi`.
You might want to unpack the zip folder.

Press the windows icon > System Variables 

### MAVEN_HOME
--> new > MAVEN_HOME

> Enter a path similar to this one: `C:\ProgramData\chocolatey\lib\maven\apache-maven-3.8.4`

### M2_HOME
--> new > M2_HOME
> Enter a path similar to this one:
`C:\ProgramData\chocolatey\lib\maven\apache-maven-3.8.4`

### Path
--> Path > new
> `%MAVEN_HOME&\bin`

## VSCODE and Maven
In order to tell Vscode the right path to your maven executive:
> open the file `C:\Users\schmalem\AppData\Roaming\Code\User\settings.json` and  change your maven path to something like this: ` "maven.executable.path": "C://ProgramData//chocolatey//lib//maven//apache-maven-3.8.4//bin//mvn",` , presuming you installed the Java Extension Pack for VSCode