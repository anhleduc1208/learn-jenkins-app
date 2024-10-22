pipeline {
    agent any
    stages {

      stage('Install bun') {
        agent {
          docker {
            image 'node:20-alpine'
            args '-u root'
            reuseNode true
          }
        }
        steps {
          sh '''
            ls -la
            node --version
            npm --version
            echo $PATH
            echo $HOME
            ls -la ~

            apk update
            apk add curl bash

            curl -fsSL https://bun.sh/install | bash

            export BUN_INSTALL=~/.bun
            export PATH=$BUN_INSTALL/bin:$PATH
            echo "export BUN_INSTALL=~/.bun" >> ~/.bashrc
            echo "export PATH=$BUN_INSTALL/bin:$PATH" >> ~/.bashrc
            #bun --version
          '''
          sh '''
            export BUN_INSTALL=~/.bun
            export PATH=$BUN_INSTALL/bin:$PATH
            echo $BUN_INSTALL
            echo $PAT
            bun --version
          '''
        }
        }
      }

      // stage('Run bun') {
      //   agent {
      //     docker {
      //       image 'node:20-alpine'
      //       args '-u root'
      //       reuseNode true
      //     }
      //   }
      //   steps {
      //     sh '''
      //       ls -la
      //       node --version
      //       npm --version
      //       echo $PATH
      //       echo $HOME
      //       ls -la ~

      //       apk update
      //       apk add curl bash

      //       curl -fsSL https://bun.sh/install | bash
      //       ls -la ~/.bun/bin/bun

      //       ~/.bun/bin/bun --version
      //     '''
      //   }
      //   }
      // }


      // stage('Build') {
      //   agent {
      //     docker {
      //       image 'node:18-alpine'
      //       reuseNode true
      //     }
      //   }
      //   steps {
      //       sh '''
      //         ls -la
      //         node --version
      //         npm --version
      //         npm ci
      //         npm run build
      //         ls -la
      //       '''
      //   }
      // }

      // stage('Test') {
      //   agent {
      //     docker {
      //       image 'node:18-alpine'
      //       reuseNode true
      //     }
      //   }
      //   steps {
      //     echo 'Test stage'
      //     sh '''
      //       ls -la
      //       ls -la
      //       if [ -f "build/index.html" ]; then
      //         echo "File exists"
      //       else
      //         echo "File doesn not exist"
      //       fi
      //       npm run test
      //     '''
      //   }
      // }

      // stage('E2E') {
      //   agent {
      //     docker {
      //       image 'mcr.microsoft.com/playwright:v1.39.0-jammy'
      //       reuseNode true
      //     }
      //   }
      //   steps {
      //     echo 'E2E test'
      //     sh '''
      //       npm i serve
      //       node_modules/.bin/serve -s build &
      //       sleep 10
      //       npx playwright test --reporter=html

      //     '''
      //   }
      // }

      
  //   }
  // post {
  //   always {
  //     junit 'jest-results/junit.xml'
  //   }
  // }
}
