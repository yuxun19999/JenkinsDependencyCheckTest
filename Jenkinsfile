pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git 'https://github.com/yuxun19999/JenkinsDependencyCheckTest.git'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {

        		dependencyCheck additionalArguments: ''' 
                    -o './'
                    -s './'
                    -f 'ALL' 
                    --prettyPrint''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
        
        		dependencyCheckPublisher pattern: 'dependency-check-report.xml'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}