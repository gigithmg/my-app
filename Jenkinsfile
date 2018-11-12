pipeline {
    agent any
    stages {
        stage('One') {
                steps {
                        echo 'Remove Previous clones from github'
			sh "sudo rm -rf /home/gigith/my-git-app"
                }
        }
	    stage('Two') {
		steps {
                        echo 'Cloning PHP Application from github'
			sh "sudo git clone https://github.com/gigithmg/my-app.git /home/gigith/my-git-app"
        	}
	    }
        stage('Three') {
                steps {
			echo 'Build Stage'
			sh "sudo php /home/gigith/my-git-app/index.php"
                        }
        }
        stage('Four') {
				steps {
					echo 'Remove OLD containers'
					sh "docker rm -f my-php-ap &> /dev/null"
					echo 'Deploying App to a docker container'
					sh "docker run -d -p 80:80 --name my-php-app -v /home/gigith/my-git-app:/var/www/html php:7.2.2-apache"
				}
                               
        }
    }
}

