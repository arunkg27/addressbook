pipeline {
    agent any
    stages {
        stage('Build') {
             agent { label 'kmaster'}
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
             agent { label 'kslave1'}
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
                echo "Welcome"
            }
        }
    }
}
