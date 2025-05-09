@Library('shared') _
pipeline {
    
    agent { label "worker" }

    stages {
        
        stage("Hello") {
            steps {
                script {
                    hello()
                }
            }
        }

        stage("Code") {
            steps {
                script {
                    clone("https://github.com/farhan24680/django-notes-app.git", "main")
                }
            }
        }

        stage("Build") {
            steps {
                script {
                    docker_build("notes-app", "latest", "farhan24680")
                }
            }
        }

        stage("Push to image docker hub") {
            steps {
                script {
                    docker_push("notes-app", "latest", "farhan24680")
                }
            }
        }

        stage("Deploy") {
            steps {
                script {
                    docker compose()
                }
            }
        }
    }
}
