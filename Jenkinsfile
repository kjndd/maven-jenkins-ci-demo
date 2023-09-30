pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Hello from build stage'
                echo 'Hello from build stage 2'

            }
        }
		
		
        stage('Deploy') {
            steps {
                echo 'Hello from deploy stage'
				//mvn install -Ptest -Dusername=$USERNAME  -Dpassword=$PASSWORD  -Dorg=eu-west1-partner20
				echo "test output"
								withCredentials([usernamePassword(credentialsId: 'apigee', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
				  sh 'echo $PASSWORD'
				  echo USERNAME
				  echo "username is $USERNAME"
				
				
				echo "username2 is ${USERNAME}"
				echo "username3 is $USERNAME"
				//sh 'mvn -f currency-v1/pom.xml install -Ptest -Dusername=' +$USERNAME + ' -Dpassword=' +$PASSWORD +' -Dorg=eu-west1-partner20'
				sh 'mvn -f currency-v1/pom.xml install -Ptest -Dusername=$USERNAME -Dpassword=$PASSWORD  -Dorg=eu-west1-partner20'
				}
            }
        }
        stage('Test') {
            steps {
                echo 'Hello from test stage'
            }
        }
        stage('Release') {
            steps {
                echo 'Hello from release stage'
            }
        }
    }
}