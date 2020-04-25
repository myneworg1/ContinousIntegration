pipeline {
    agent any 
	
    stages {
        stage('Maven Compile') { 
            steps {
	        withMaven(maven : 'mymaven') {
		     sh 'mvn clean compile'
	        }
                
            }
        }
        stage('Maven Test') { 
            steps {
	       withMaven(maven : 'mymaven') {
	           sh 'mvn test'
               }
            }
        }
        stage('Maven Package') { 
            steps {
                withMaven(maven : 'mymaven') {
	             sh 'mvn package'
            }
        }
    }
	stage('docker build ') { 
            steps {
	             sh 'docker build -t hw .'
            }
        }
	 stage('docker images') { 
            steps {
	             sh 'docker images'
            }
        }
         
	    stage('docker tag') { 
            steps {
	             sh 'docker tag hw gcr.io/mystic-impulse-245222/hw:1.0'
            }
        }
	    
	    stage('docker push') { 
            steps {
	             sh 'docker push gcr.io/mystic-impulse-245222/hw:1.0'
            }
        }
      


   }
}
