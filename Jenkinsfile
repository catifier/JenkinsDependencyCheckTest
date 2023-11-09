	pipeline {
	    agent any
	    stages {
	        stage('OWASP-DC') {
		      steps {
			dependencyCheck additionalArguments: ''' 
				    -o './'
				    -s './'
				    -f 'ALL' 
				    --prettyPrint''', odcInstallation: 'OWASP-DC'
			
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		      }
		    }
	    }
	    post {
		always {
		    // Publish the OWASP Dependency-Check report
		    step([$class: 'DependencyCheckPublisher', pattern: '**/dependency-check-report.xml'])
		}
	    }
	}

