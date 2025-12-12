pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
		sh '/var/lib/jenkins/.sdkman/candidates/maven/current/bin/mvn -B -DskipTests clean package'
            }
        }
		stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
