pipeline {
  agent any
  stages {
    stage('Server') {
      parallel {
        stage('Server') {
          agent {
            docker {
              image 'maven:3.3.9-jdk-8'
              args '-u 0;0'
            }

          }
          steps {
            sh '''echo "building"
mvn --version
mkdir -p target
touch "target/server.war"'''
            stash(name: 'server', includes: '**/*.war')
          }
        }

        stage('client') {
          agent {
            docker {
              image 'node:6'
              args '-u 0:0'
            }

          }
          steps {
            sh '''echo "building client"
npm install --save react
mkdir -p dist
cat > index.html <<EOF
hello !
EOF
touch "dist/client.js"'''
          }
        }

      }
    }

  }
}