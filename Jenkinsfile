pipeline{
	agent any
	stages{
		//here we are pulling the latest image from the repo
		//otherwise if you don't pull, docker will always use the local image it had pulled initially for all the tests
		stage("Pull Latest Image"){
			steps{
				bat "docker pull priya2298/selenium-docker"
			}
		}
		
		//Here we run the grid seperately
		//using the -d command we run it in the background
		//And only select the Hub, Chrome, and Firefox images to run from the docker-compose file
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
			
			
		}
	}
}
