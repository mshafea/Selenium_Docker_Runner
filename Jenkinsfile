pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull mohshafea/selenium-docker"
			}
		}
		stage("Start Grid"){
			steps{
				sh "docker-compose up -d --no-colors hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up search-module book-flight-module"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
			// sh "sudo rm -rf output/"
		}
	}
}
