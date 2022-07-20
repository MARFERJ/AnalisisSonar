pipeline {
   agent any
   stages {
	stage('Sonarqube') {
    	   environment {
        	scannerHome = tool 'SonarScanner'
    	   }
    	   steps {
        	withSonarQubeEnv('SonarServer') {
            	sh "${scannerHome}/sonar-scanner"
        	}
        	timeout(time: 10, unit: 'MINUTES') {
            	waitForQualityGate abortPipeline: true
        	}
    	   }
	}
        stage ('Paso Hola') {
              steps {
                echo 'Hello Mundo!'
              }
	}
	stage ('Ejecutar comandos') {
              steps {
                  bat 'hostname'
	      }
        }
    }
}
