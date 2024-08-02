 pipeline {
    agent any

    stages {
        stage('Run secuirty tests'){
          steps {
		script {
              		echo "Running Security Testing..."

                        sh 'pip install bandit'
                        sh 'bandit -r .'
			}
          }
        }

        stage('Create Image'){
          steps {
		script {
            		echo "Creating Image..."
          		sh 'docker build -t My-Flask-App-pipeline  .'
			}
		}
        }

        stage('Run Security scans'){
          steps{
		script{

	            echo "Running Security Scans..."
		      sh 'trivy image My-Flask-App-pipeline'
			}

          }
        }

        stage('Upload image'){
          steps{
		script {
           	       echo "Uploading image..."
           	       docker push alielbassiouny/my-flask-app-pipeline

         	
		}
		 }
        }
    }
}

