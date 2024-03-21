pipeline {
    agent any
    stages {
        stage("deployment") {
            steps {
                script {
                    sh 'tar -cvzf dist.tar.gz *'
                    sh 'scp dist.tar.gz jenkins@65.2.29.148:/var/www/html/team1-fe/'
                    sh 'ssh jenkins@65.2.29.148 "cd /var/www/html/team1-fe/ && tar -xvzf dist.tar.gz"'
                    sh 'ssh jenkins@65.2.29.148 "cd /var/www/html/team1-fe/ && sudo chown -R jenkins:jenkins *"'
                    sh 'ssh jenkins@65.2.29.148 "cd /var/www/html/team1-fe/ && npm install --legacy-peer-deps"'
					sh 'ssh jenkins@65.2.29.148 "cd /var/www/html/team1-fe/ && npm install vite"'
                    sh 'ssh jenkins@65.2.29.148 "cd /var/www/html/team1-fe/ && npm run build"'
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
