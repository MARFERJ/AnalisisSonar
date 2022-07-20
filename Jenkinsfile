pipeline {
    agent any
        
    stages {

      node {
        stage('SCM') {
          checkout scm
        }
        stage('SonarQube Analysis') {
          def scannerHome = tool 'SonarScanner';
          withSonarQubeEnv() {
            sh "${scannerHome}/bin/sonar-scanner"
          }
        }
        stage ("Sonar: Espera a respuesta de Sonar por escaneo") {
              steps {
                // Wait for QuaityGate webhook result
                timeout(time: 1, unit: 'HOURS') {
		   waitForQualityGate abortPipeline: true
                }
	      }
	}
        stage('Paso Hola') {
              steps {
                echo 'Hello Mundo!'
              }
	}
	stage('Ejecutar comandos') {
              steps {
                  bat 'hostname'
	      }
        }
      }
    }
}
