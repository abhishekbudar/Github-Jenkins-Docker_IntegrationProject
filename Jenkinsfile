// Below is a Scripted Pipleine approach

// Declartive pipeline
pipeline {
	agent any
	//agent { docker {image 'maven:3.6.3'}}

	//environment {
   //     dockerHome = tool 'myDocker'
	//	mavenHome = tool 'myMaven'
   //		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
    //}
	stages {
		stage('Production'){
			steps {
				
				if sudo docker ps | grep production_server
				then
				echo "Production server already running"
				else
				sudo docker run -d -t -i -p 8081:80 -v /production:/usr/local/apache2/htdocs/ --name production_server httpd
				fi
				sudo cp -r -v -f * /production/

			
			}
		}
	}
	// 	stage ('Compile'){
	// 		steps {
	// 			sh "mvn clean compile" //downloads dependemncies and compile your code
	// 		}

	// 	}
	// 	stage('Test'){
	// 		steps {
	// 			sh "mvn test"  // run your unit test
	// 		}
	// 	}
	// 	stage('IntegrationTest'){
	// 		steps {
	// 			sh "mvn failsafe:integration-test failsafe:verify"
	// 		}
	// 	}
	// 	stage('Pacakage '){
	// 		steps {
	// 			sh "mvn package -DskipTests"
	// 		}
	// 	}
	// 	stage('Build Docker Image') {
	// 		steps{
	// 			//docker build -t in28min/currency-exchange-devops:$env.Build_Tag
	// 			script {
	// 				dockerImage = docker.build("in28min/currency-exchange-devops:${env.Build_Tag}")
	// 			}
	// 		}
	// 	}
	// 	stage('Push Docker Image') {
	// 		steps{
	// 			script{
	// 				docker.withRegistry('','dockerhub'){
	// 				dockerImage.push();
	// 				dockerImage.push('latest');
	// 				}
	// 			}
	// 		}
	// 	}
	// } 
	post {
		// always{
		// 	echo 'I am awesome, I know Jenkins'
		// }
		success {
			echo 'When sucessful'
		}
		failure{
			echo 'When fail'
		}
	}
		
}

	