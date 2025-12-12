pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
		sh '/var/lib/jenkins/.sdkman/candidates/maven/current/bin/mvn -B -DskipTests clean package'
            }
        }
    }
}
