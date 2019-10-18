pipeline {
  agent any
  stages {
    stage('Compilar') {
      steps {
        withMaven(globalMavenSettingsFilePath: 'C:\\Users\\alumno.41\\Documents\\Jenkins - Alumno\\maven\\conf\\settings.xml', jdk: 'jdk1.8.0_112', maven: 'maven', mavenSettingsFilePath: 'C:\\Users\\alumno.41\\Documents\\Jenkins - Alumno\\maven\\conf\\settings.xml') {
          bat 'mvn clean install -DskipTests'
        }

      }
    }
  stage('Deploy') {
     steps {
        deploy adapters: [tomcat7(credentialsId: 'a31d2b2e-d27b-4cbc-a848-d799ded7645d', path: '', url: 'http://localhost:8082')], contextPath: 'WebPrueba', war: 'target/*.war'
      }
   }
  }
}