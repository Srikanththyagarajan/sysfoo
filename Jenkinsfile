pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compile maven app'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'test maven app'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      parallel {
        stage('package') {
          steps {
            echo 'package maven app'
            sh 'mvn package -DskipTests'
          }
        }

        stage('') {
          steps {
            archiveArtifacts 'target/*war'
          }
        }

      }
    }

  }
  tools {
    maven 'Maven3.6.3'
  }
}