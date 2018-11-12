pipeline {
    agent any
    stages {
        stage('One') {
                steps {
                        echo 'Remove Previous clones from github'
			rm -rf my-app
                }
        }
	    stage('Two'){
		    
		steps {
                        echo 'Cloning PHP Application from github'
			git clone https://github.com/gigithmg/my-app.git
        }
	    }
        stage('Three') {
                steps {
			echo "Build Stage"
			php my-app/index.php
                        }
        }
        stage('Four') {
                        agent {
                                docker {
                                        reuseNode false
					image 'php:7.2.2-apache'
                                        }
			}
				steps {
					echo 'Remove old containers'
					sudo docker rm -f my-php-app	
					echo 'Deploying App to a docker container'
					sudo docker run -d -p 80:80 --name my-php-app -v /home/gigith/my-app:/var/www/html php:7.2.2-apache
				}
                               
        }
    }
}

