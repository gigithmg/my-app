pipeline {
    agent any
    stages {
        stage('One') {
                steps {
                        echo 'Hi, this is stage One'
			
                }
        }
	    stage('Two'){
		    
		steps {
			echo 'Hi. this is stage Two'
        }
	    }
        stage('Three') {
                steps {
			echo "Hello stage Three"
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
					echo 'Running the integration test..'
				}
                               
        }
    }
}

