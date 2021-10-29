pipeline {
    agent any
    stages {
        stage("Clean up") {
            steps {
                deleteDir();
            }
        }
        stage("Clone repo") {
            steps {
                bat "git clone https://github.com/terry-fee/gs-rest-service"
            }
        }
		stage("Create properties file") {
			steps {
				dir("gs-rest-service/complete/src/main") {
				    bat "mkdir resources || echo"
				}
				dir("gs-rest-service/complete/src/main/resources") {
				    bat "echo server.port=8083 > application.properties"
				}
			}
		}
        stage("Build and Test") {
            steps {
		dir("gs-rest-service/complete") {
			bat "mvn clean && mvn install package"
		}
            }
        }
    }
}
