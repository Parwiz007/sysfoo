pipeline {
    agent any
    tools{
       maven 'Maven 3.9.11'
    }  

    stages {
        stage("build") {
            steps {
                echo 'Compiling sysfoo app...'
                sh 'mvn compile'
            }
        }

        stage("test") {
            steps {
                echo 'running unit test'
                sh 'mvn clean test'
            }
        }

        stage("package") {
            steps {
                echo 'step 3'
             sh 'mvn package -DskipTests'
            }
        }
    }

    post {
        always {
            echo 'This pipeline is completed..'
        }
    }
}
