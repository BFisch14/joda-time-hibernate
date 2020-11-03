pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Deploy') {
            environment {
                Art_COMMON_CREDS = credentials('artifactory')
            }
            steps {
               sh 'curl -u $Art_COMMON_CREDS -X PUT "http://artifactory:8081/artifactory/libs-snapshot-local/com/devops-bootcamp/samples/joda-time898/joda-time-hibernate/1.7-SNAPSHOT/joda-time-hibernate-1.7-1.jar" -T ${WORKSPACE}/target/joda-time-hibernate.jar' 
            }
        }
    }
}