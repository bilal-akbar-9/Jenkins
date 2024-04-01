pipeline {

    agent any

    tools {nodejs "nodejs-20"} 
    
    stages {
         stage('build') {
          steps {
              sh 'npm install'
            }
          }
         stage('Initialize'){
            def dockerHome = tool 'myDocker'
            env.PATH = "${dockerHome}/bin:${env.PATH}"
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
