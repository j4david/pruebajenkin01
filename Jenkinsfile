pipeline {
  agent any
  stages {
    stage('Compilar') {
      steps {
        withMaven(globalMavenSettingsFilePath: 'C:\\Users\\alumno.41\\Documents\\Jenkins - Alumno\\maven\\conf\\settings.xml', jdk: 'JDK', maven: 'Maven', mavenSettingsFilePath: 'C:\\Users\\alumno.41\\Documents\\Jenkins - Alumno\\maven\\conf\\settings.xml') {
          bat 'mvn clean install -DskipTests'
        }

      }
    }
    stage('Deploy') {
      steps {
        deploy(adapters: [tomcat7(credentialsId: 'a31d2b2e-d27b-4cbc-a848-d799ded7645d', path: '', url: 'http://localhost:8082')], contextPath: 'WebPrueba', war: 'target/*.war')
      }
    }
    stage('Test') {
      steps {
        withMaven(globalMavenSettingsFilePath: 'C:\\Users\\alumno.41\\Documents\\Jenkins - Alumno\\maven\\conf\\settings.xml', mavenSettingsFilePath: 'C:\\Users\\alumno.41\\Documents\\Jenkins - Alumno\\maven\\conf\\settings.xml', maven: 'Maven', jdk: 'JDK') {
          bat 'mvn test -Dmaven.test.failure.ignore=true'
        }

      }
    }
    stage('sonar') {
      steps {
        withSonarQubeEnv('sonar') {
          withMaven(globalMavenSettingsFilePath: 'C:\\Users\\alumno.41\\Documents\\Jenkins - Alumno\\maven\\conf\\settings.xml', mavenSettingsFilePath: 'C:\\Users\\alumno.41\\Documents\\Jenkins - Alumno\\maven\\conf\\settings.xml', jdk: 'JDK', maven: 'Maven') {
            bat 'mvn sonar:sonar -Duser.home=/data/jenkins/ -Dmaven.test.failure.ignore=true'
          }

        }

      }
    }
  }
}