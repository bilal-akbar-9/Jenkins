pipeline {

    agent any

    tools {nodejs "nodejs-20"} 
    
    stages {
         stage('Checkout') {
            steps {
            script {
                sh '''
                if [ ! -d "newDirectory" ]; then
                    git clone https://github.com/bilal-akbar-9/Jenkins/
                fi
                '''
                }
            }
        }

         stage('build') {
          steps {
              sh 'npm install'
            }
          }
        stage('test') {
          steps {
              sh 'npm run test'
            }
          }
         stage('Initialize'){
            steps{
                script{
                def dockerHome = tool 'myDocker'
                env.PATH = "/usr/bin/docker"
                }
            }
        }

        
        stage('Docker Comopse Up') {
            steps {
               
                    sh "docker compose up"
                
            }
        }
         stage('kill') {
            steps {
               
                    sh "docker compose down"
                
            }
        }
    }
}
