
node {
   def mvnHome
   def version 
   stage('Preparation') {
      git 'https://github.com/sourabh0205/addressbook.git'
      mvnHome = tool 'maven'
	  version = '2.3.5' 
   }
   stage('Build') {
         {

      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore test -Pfunctional-test -DSkipUTs=true -DskipTests=true"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore test -Pfunctional-test -DSkipUTs=true -DskipTests=true/)
      }
    } // withMaven will discover the generated Maven artifacts, JUnit reports and FindBugs reports
    

   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
     stage('DeployToServer') {
	 } 
}
