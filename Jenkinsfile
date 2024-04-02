pipeline {
  agent any
  tools { 
      maven 'aughh' 
      jdk 'augh' 
  }
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/Keraisyn/maven-samples-A6.git', branch: 'master')
      }
    }

    stage('clean') {
      steps {
        sh 'mvn clean'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'mvn test'
          }
        }

        stage('bisect') {
          steps {
            sh '''git bisect HEAD 98ac319c0cff47b4d39a1a7b61b4e195cfa231e5
git bisect run mvn clean test'''
          }
        }

      }
    }

  }
}
