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
  }
}