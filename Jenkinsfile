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
              ls -la
              if [-f build/index.html]; then
                echo "File exists"
              else
                echo "File doesn not exist"
              fi
              npm run test
            '''
          }
        }
    }
}
