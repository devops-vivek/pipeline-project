def artifactname = "sp-boot-app.jar"
def repoName = "sp-boot-app-repo"
def pipelineName = "devops_vk_pipeline"
def semanticVersion = "${env.BUILD_NUMBER}.0.0"
def packageName = "spboot-package_${env.BUILD_NUMBER}"
def version = "${env.BUILD_NUMBER}.0"
/////def orchToolId="1153dbd753f100107109ddeeff7b122e"  
//${env.BUILD_NUMBER}
pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage("checkout") {
            stages{
                stage('deploy to dev') {
                    when{
                        branch 'dev'
                    }
                    steps{
                        echo "Building in UAT"
                    }
                }
                stage('deploy to prod') {
                    when {
                        branch 'master'
                    }
                    steps{
                        echo "Building in prod"
                    }
                }
	    }
	}

        stage("build") {
            stages{
                stage('deploy to dev') {
                    when{
                        branch 'dev'
                    }
                    steps{
                        echo "Manual Building in UAT"
			snDevOpsChange(configurationName:"DevOps-empvkvan105.service-now.com-1707348345658")
                    }
                }
                stage('deploy to prod') {
                    when {
                        branch 'master'
                    }
                    steps{
                        echo "Manual Building in prod"
                    }
                }
	    }

        }

        stage('unit-tests') {
            stages{
                stage('deploy to dev') {
                    when{
                        branch 'dev'
                    }
                    steps{
                        echo "Manual Test in UAT"
                    }
                }
                stage('deploy to prod') {
                    when {
                        branch 'master'
                    }
                    steps{
                        echo "Manual Test in prod"
                    }
                }
	    }
        }

        stage("deploy") {
            stages{
                stage('deploy to dev') {
                    when{
                        branch 'dev'
                    }
                    steps{
                        echo "deploy in UAT"
                    }
                }
                stage('deploy to prod') {
                    when {
                        branch 'master'
                    }
                    steps{
                        echo "deploy in prod"
			snDevOpsChange()

                    }
                }
            }
        }
	
    }

}
