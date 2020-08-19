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
                      sh 'ls -l'
                      echo 'address apps: http://127.0.0.1:3000'
                      input {
                        message "Finished using the web site? (Click "Proceed" to continue)"
                        ok  "Yes, continue"
                        submitter "Abort"
                        parameters {
                          string(name: 'NAME', defaultValue: 'NGUYEN VAN A', description: 'name of person submit for project')
                          string(name: 'DEPARTMENT', defaultValue: 'IT', description: 'name department of person submit for project')
                          text(name:'USER', description: 'User login jenkins pipline')
                          password(name: 'PASSWORD', description: 'password user login')
                        }
                      }
                      echo 'you are ${params.NAME} department ${params.DEPARTMENT} submit this project'
                      
                    }     
              }
        }
}