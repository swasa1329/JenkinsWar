node{

   /* def tomcatWeb = 'D:\\Auto_deployment\\apache-tomcat-9.0.30\\apache-tomcat-9.0.30\\webapps' */
   
   def tomcatWeb = 'C:\\Users\\HP\\OneDrive\\Desktop\\DevOps\\apache-tomcat-7.0.94\\webapps'
   
   /* def tomcatBin = 'D:\\Auto_deployment\\apache-tomcat-9.0.30\\apache-tomcat-9.0.30\\bin' */
   
   def tomcatBin = 'C:\\Users\\HP\\OneDrive\\Desktop\\DevOps\\apache-tomcat-7.0.94\\bin'
   
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/swasa1329/JenkinsWar.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'Maven', type: 'maven'   
      bat "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     bat "copy target\\JenkinsWar.war \"${tomcatWeb}\\JenkinsWar.war\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat start"
         sleep(time:200,unit:"SECONDS")
   }
}
