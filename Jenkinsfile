node {
   def mvnHome
   stage('Preparation') {
      git 'https://github.com/sourabh0205/addressbook.git'
      mvnHome = tool 'maven'
   }
   }
stage('UNITTEST') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore test -Pfunctional-test -DSkipUTs=true -DskipTests=true"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
stage('Review') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn'pmd:pmd"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }

   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
}   
}
