pipeline {
    agent any
    stages {
        stage('One') {
                steps {
                        echo 'Remove Previous clones from github'
			sh "rm -rf my-app"
                }
        }
	    stage('Two') {
		steps {
                        echo 'Cloning PHP Application from github'
			sh "git clone https://github.com/gigithmg/my-app.git"
        	}
	    }
        stage('Three') {
                steps {
			echo 'Build Stage'
			sh "php my-app/index.php"
                        }
        }
	stage('Four') {
                steps {
                        echo 'Remove Previous docker containers'
                        sh "docker rm -f my-php-app"
                        }
        }
        stage('Five') {
                        agent {
                                docker {
                                        reuseNode false
					image 'php:7.2.2-apache'
					args '-p 80:80 --name my-php-app -v /home/gigith/my-app:/var/www/html'
                                        }
			}
				steps {
					echo 'Deployed App to a docker container'
				}
                               
        }
    }
}

