@Library("Shared") _
pipeline {
    agent { label 'worker' }

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
                    clone(repoUrl: "https://github.com/Sufiyan12421/Full-Stack-Notes-App.git", branch: "main")
                }
            }
        }

        stage("Build") {
            steps {
                script {
                    docker_build(imageName: "notesapp", imageTag: "latest", user: "sufiyn")
                }
            }
        }

        stage("Push to DockerHub") {
            steps {
                script {
                    docker_push(imageName: "notesapp", imageTag: "latest", user: "sufiyn")
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "🚀 This is Deploying the Code"
                sh "docker compose up -d"
            }
        }
    }
}
