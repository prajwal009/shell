pipeline {
  agent any
  stages {
    stage('Server') {
      agent {
        docker {
          image 'maven:3.3.9-jdk-8'
        }

      }
      steps {
        sh '''echo "hello"
mvn --version
var = `mvn --version`
echo $var'''
      }
    }

  }
}