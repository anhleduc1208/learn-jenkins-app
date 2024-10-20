pipeline {
    agent {
      any
    }
    stages {
      stage('Build') {
        agent {
          docker {
            image 'node:18-alpine'
            reuseNode true
          }
        }
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
        agent {
          docker {
            image 'node:18-alpine'
            reuseNode true
          }
        }
        steps {
          echo 'Test stage'
          sh '''
            ls -la
            ls -la
            if [ -f "build/index.html" ]; then
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
