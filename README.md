
# Analyse Sample Project with SonarQube 
###### Powered By,
[![N|Solid](http://www.voyalab.com/wp-content/uploads/2016/10/completeLogo-e1476280430173.png)](http://voyalab.com)

### Pre-requisite
 - [SonarQube][sonarqube]
 - [SonarQube Scanner][sonarqubescanner]

##### In this we will analyse one sample project with SonarQube and SonarQube scanner. Make sure your configuration of SonarQube server and SonarQube Scanner is done. If not, refer [SonarQube] and [SonarQube Scanner][sonarqubescanner] installation guide.
###### I am using one example project which I have forked on my github account. It is a simple MEAN app.For analysing projects with SonarQube you must have all necessary language plugins installed on your server.

## Installing Plugins 
 - Login as Administrator in SonarQube Server 
 - Click on administration tab 
 - Click on System it will give dropdown menu. 
 - Click on Update Center 
[![N|Solid](http://www.voyalab.com/wp-content/uploads/2016/10/Screenshot-from-2016-10-12-17-43-47.png)](http://www.voyalab.com/wp-content/uploads/2016/10/Screenshot-from-2016-10-12-17-43-47.png)
 - You can see all installed and available plugins.
 - According to your project install those plugins.
 [![N|Solid](http://www.voyalab.com/wp-content/uploads/2016/10/Screenshot-from-2016-10-12-18-00-46.png)](http://www.voyalab.com/wp-content/uploads/2016/10/Screenshot-from-2016-10-12-18-00-46.png)
 - Now your server is capable of analysing projects with those installed plugins.

## Configuring sonar-project.properties file
 - Sonar-runner (now sonar-scanner) is default launcher to anlayse project with SonarQube.
 - Create Configuration file in root direcctory of project. 
 - For sample we are using one example project from our [github](https://github.com/voyalab).
 - Configuration file consist ,
   ```sh
     # must be unique in a given SonarQube instance
     sonar.projectKey=my:project
     # this is the name and version displayed in the SonarQube UI. Was mandatory      prior to SonarQube 6.1.
     sonar.projectName=My project
     sonar.projectVersion=1.0
     # Path is relative to the sonar-project.properties file. Replace "\" by "/"      on Windows.
     # Since SonarQube 4.2, this property is optional if sonar.modules is set. 
     # If not set, SonarQube starts looking for source code from the directory       containing 
     # the sonar-project.properties file.
     sonar.sources=.
 
     # Encoding of the source code. Default is default system encoding
     #sonar.sourceEncoding=UTF-8
     ```
 - For our sample project , you can clone project from [here](https://github.com/voyalab/loopback-angular-admin)
 - In root directory create sonar-project.properties ,
    ```sh
    #This is sonar properties file. Sonar-runner will understand different parameters for analysis with this file
    #You will get complete parameters list at         http://docs.sonarqube.org/display/SONAR/Analysis+Parameters

    #Parameters start
    #Sonar host url - used for making connection with server
    sonar.host.url = http://localhost:9000/sonar

    #Project related mandotary parameters
    sonar.projectKey = LoopbackAngularMaster
    sonar.projectName = LoopbackDemo
    sonar.projectVersion = 1.0

    #Comma-separated paths to directories containing source files.
    sonar.sources = client , common , server

    #Project configuration Parameters
    sonar.projectDescription = Its an example angular app forked from github.

    #Set the source file encoding.Encoding of source files. Example of values:     UTF-8, MacRoman, Shift_JIS.
    sonar.sourceEncoding = UTF-8

    #Set analysis language
    #Set the language of the source code to analyze. Browse the     http://docs.sonarqube.org/display/PLUG/Plugin+Library page to get the list of   all available languages.
    #If not set, a multi-language analysis will be triggered.
    #sonar.language = Javascript , CSS
    #Commented beacuse We want to set multi language analysis 
    ```
 - Run sonar-runner or sonar-scanner 
    ```sh 
    $ sonar-scanner 
    ```
 - Sample Output :
 [![N|Solid](http://www.voyalab.com/wp-content/uploads/2016/10/Screenshot-from-2016-10-12-14-14-32.png)](http://www.voyalab.com/wp-content/uploads/2016/10/Screenshot-from-2016-10-12-14-14-32.png)
[![N|Solid](http://www.voyalab.com/wp-content/uploads/2016/10/Screenshot-from-2016-10-12-14-14-41.png)](http://www.voyalab.com/wp-content/uploads/2016/10/Screenshot-from-2016-10-12-14-14-41.png)
[![N|Solid](http://www.voyalab.com/wp-content/uploads/2016/10/Screenshot-from-2016-10-12-14-14-52.png)](http://www.voyalab.com/wp-content/uploads/2016/10/Screenshot-from-2016-10-12-14-14-52.png)

 - You can avoid potential risk by adapting sonarqube.
 
   [sonarqube]:<http://www.voyalab.com/2016/10/06/install-sonarqube-ubuntu/>
   [sonarqubescanner]:<http://www.voyalab.com/2016/10/08/installing-sonarqube-scanner/>
   
