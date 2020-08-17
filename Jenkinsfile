pipeline {
        agent {
              docker {
                    image 'node:12'
                    args '-p 3000:3000'
              }
        }
        triggers {
              pollSCM('H H(8-17)/2 * 1-11 1-5')
        }
        stages {
              stage('build') {
                    steps {
                         echo 'check version nodejs:'
                         sh 'node --version'
                    }
              }
              stage('Test code') {
                    steps {
                         sh 'node ./app.js & sleep 60'
                         input message: 'Finished using the web site? (Click "Proceed" to continue)'        
                    }     
              }
        }
}
