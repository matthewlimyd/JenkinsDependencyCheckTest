pipeline {
  agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git 'https://github.com/matthewlimyd/JenkinsDependencyCheckTest.git'
			}
		}

		stage('OWASP Dependency-Check Vulnerabilities') {
            steps {
                dependencyCheck additionalArguments: ''' 
                    -o './'
                    -s './'
                    -f 'ALL' 
                    --disableAssembly
                    --disableYarnAudit
                    --prettyPrint
                ''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'

                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
            }
        }
}
}
