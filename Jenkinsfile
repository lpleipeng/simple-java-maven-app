pipeline {
    agent any
    stages {
        // 构建阶段：使用 Maven 3.9.6 绝对路径
        stage('Build') {
            steps {
                sh '/var/lib/jenkins/.sdkman/candidates/maven/current/bin/mvn -B -DskipTests clean package'
            }
        }
        // 测试阶段：统一 Maven 路径
        stage('Test') {
            steps {
                sh '/var/lib/jenkins/.sdkman/candidates/maven/current/bin/mvn test'
            }
        }
        // 交付阶段：示例打包操作（可根据需求修改）
        stage('Deliver') {
            steps {
                echo 'Build success! Preparing delivery...'
                sh 'ls -l target/*.jar' // 查看构建产物
            }
        }
    }
    post {
        always {
            junit '**/target/surefire-reports/*.xml' // 测试报告收集
            cleanWs() // 清理工作空间（可选）
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed! Check logs for details.'
        }
    }
}
