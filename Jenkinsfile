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
        deploy(adapters: [tomcat7(credentialsId: 'a31d2b2e-d27b-4cbc-a848-d799ded7645d', path: '', url: 'http://localhost:8082')], contextPath: 'WebPrueba', war: 'target/*.war')
      }
    }
    stage('Test') {
      steps {
        withMaven(globalMavenSettingsFilePath: 'C:\\Users\\alumno.41\\Documents\\Jenkins - Alumno\\maven\\conf\\settings.xml', mavenSettingsFilePath: 'C:\\Users\\alumno.41\\Documents\\Jenkins - Alumno\\maven\\conf\\settings.xml', maven: 'maven', jdk: 'jdk1.8.0_112') {
          bat 'mvn test -Dmaven.test.failure.ignore=true'
        }

      }
    }
    stage('Cobertura') {
      steps {
        cobertura(coberturaReportFile: 'target\\surefire-reports\\cobertura\\coverage.xml', conditionalCoverageTargets: '70, 0, 0', lineCoverageTargets: '80, 0, 0', methodCoverageTargets: '80, 0, 0', sourceEncoding: 'ASCII')
      }
    }
  }
}