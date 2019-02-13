pipeline {
    agent any
    stages {
        stage('Clone Front A-B') {
            steps {
                sh "git clone https://github.com/ScastellanosM/movie-analyst-ui.git"
                sh "rm -rf movie-analyst-ui"
            }
        }
        stage('Build'){
            steps {
                sh "zip -r movie-analyst-ui.zip /var/lib/jenkins/workspace/FrontA_master"   
                sh "zip -r movie-analyst-ui.zip /var/lib/jenkins/workspace/FrontB_master"    
            }
        }
        stage('Deploy Front Server A'){
            steps {
               sh "scp -i /home/ubuntu/SantiagoCastellanos.pem /var/lib/jenkins/workspace/FrontA_master/movie-analyst-ui.zip ubuntu@11.0.1.17:/home/ubuntu"
           }
        }  
        stage('Deploy Front Server B'){
            steps {
               sh "scp -i /home/ubuntu/SantiagoCastellanos.pem /var/lib/jenkins/workspace/FrontB_master/movie-analyst-ui.zip ubuntu@11.0.2.108:/home/ubuntu"
           }
        } 
       /* stage('Deploy Back Server '){
            steps {
               sh "scp -i /home/ubuntu/SantiagoCastellanos.pem /var/lib/jenkins/workspace/FrontA_master/movie-analyst-ui.zip ubuntu@11.0.1.17:/home/ubuntu"
           }
        }*/     
    }
}
  