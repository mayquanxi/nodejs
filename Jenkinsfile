pipeline {
        agent {
              docker {
                    image 'node:12'
                    label 'akali'
                    args '-p 3000:3000'
              }
        }
        triggers {
              pollSCM('H  H(6-18)/2 * * 1-6')
        }
        stages {
              stage('build and install dependences') {
                    steps {
                      echo "THis is BUILD stage"
                      echo ""
                      sh 'npm install'
                    }
              }
              stage('Test') {
                    steps {
                      echo "This is TEST stage"
                      echo ""
                    
                      sh 'npm start & sleep 5'
                      sh 'echo $! >./pidfile'
                      echo 'address apps: http://127.0.0.1:3000'
                      input message: 'Finished using the web site? (Click "Proceed" to continue)'
                      sh 'kill $(cat ./pidfile)'
                    }     
              }
        }
}