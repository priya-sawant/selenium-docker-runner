pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				bat "docker pull priya2298/selenium-docker"
			}
		}
		stage("Start Grid"){
			steps{
				bat "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose up testng-module"
			}
		}
	}
	post{
		always{
			
			bat "docker-compose down"
			bat "sudo rm -rf output/"
			
		}
	}
}
