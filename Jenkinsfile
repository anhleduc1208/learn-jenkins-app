pipeline {
    agent {
      docker {
        image 'node:18-alpine'
        reuseNode true
      }
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                  ls -la
                  node --version
                  npm --version
                  npm ci
                  npm run build
                  ls -la
                '''
            }
        }

        stage('Test') {
          steps {
            echo 'Test stage'
            sh '''
              ls -la
              cd build
              ls -la
              if [-f "index.html"]; then
                echo "File exists"
              else
                echo "File doesn not exist"
              fi
            '''
          }
        }
    }
}
