pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                // 必须带 Maven 3.9.6 绝对路径，不能只写 mvn
                sh '/var/lib/jenkins/.sdkman/candidates/maven/current/bin/mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                // 同样用绝对路径，和 Build 阶段保持一致
                sh '/var/lib/jenkins/.sdkman/candidates/maven/current/bin/mvn test'
            }
           post {
                always {
            		junit '**/target/surefire-reports/*.xml'
       			 }
    		}'
	}
	stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
            }
        }
     }
}
