pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'Compiling sysfoo app...'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'running unit test'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'step 3'
        sh '''# Truncate Git commit to first 7 characters
GIT_SHORT_COMMIT=$(echo $GIT_COMMIT | cut -c 1-7)

# Set Maven version using the short commit
mvn versions:set -DnewVersion="$GIT_SHORT_COMMIT"
mvn versions:commit'''
        sh 'mvn package -DskipTests'
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'Maven 3.9.11'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}