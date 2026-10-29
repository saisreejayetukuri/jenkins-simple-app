pipeline {
    agent any
    
    stages {
        stage('Checkout Code') {
            steps {
                // Pulls the latest code from GitHub
                checkout scm
            }
        }
        
        stage('Deploy Application') {
            steps {
                // Kills the old server if it is running, then starts the new one on port 8000
                sh '''
                    pkill -f "python3 -m http.server 8000" || true
                    nohup python3 -m http.server 8000 > server.log 2>&1 &
                '''
            }
        }
    }
}
