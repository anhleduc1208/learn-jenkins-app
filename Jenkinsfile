pipeline {
    agent any
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

      stage('E2E') {
        agent {
          docker {
            image 'mcr.microsoft.com/playwright:v1.39.0-jammy'
            reuseNode true
          }
        }
        steps {
          echo 'E2E test'
          sh '''
            npm i serve
            node_modules/.bin/serve -s build &
            sleep 10
            npx playwright test --report=html
            
          '''
        }
      }

      
    }
  post {
    always {
      junit 'jest-results/junit.xml'
    }
  }
}
