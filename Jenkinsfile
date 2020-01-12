pipeline {
   agent any

   tools {
      maven "M2_HOME"
   }

   stages {
      stage('Build') {
         steps {
            checkout scm
            sh "mvn -Dmaven.test.failure.ignore=true clean package"

         }

         post {
            success {
               junit '**/target/surefire-reports/TEST-*.xml'
               archiveArtifacts 'target/*.war'
            }
         }
      }
   }
}
