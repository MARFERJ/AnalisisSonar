pipeline {
   agent any
   stages {
	stage('Sonarqube') {
    	   environment {
        	scannerHome = tool 'SonarScanner'
    	   }
    	   steps {
        	withSonarQubeEnv('SonarServer') {
            	sh "${scannerHome}sonar-scanner.bat \
		    -Dsonar.projectKey=MARFERJ \
		    -Dsonar.sources=. \
		    -Dsonar.host.url=http://ses000a108259:9000"
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
