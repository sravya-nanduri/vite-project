pipeline{
		agent any{
				stages{
					stage("deployment"){
						steps{
						script{
							sh 'tar -cvzf dist.tar.gz *'
							sh 'scp jenkins@65.2.29.148:/var/www/html/team1-fe/'
							sh 'ssh jenkins@65.2.29.148 "cd /var/www/html/team1-fe/ && tar -xvzf dist.tar.gz"'
							sh 'ssh jenkins@65.2.29.148 "cd /var/www/html/team1-fe/ && sudo chown -R jenkins:jenkins *"'
							sh 'ssh jenkins@65.2.29.148 "cd /var/ww/html/team1-fe/ && npm install"'
							sh 'ssh jenkins@65.2.29.148 "cd /var/www/html/team1-fe/ && npm run buid"'
							}
							}
					}
				}
    }
	post{
		 always{
			cleanWS()
		 }
	}
}