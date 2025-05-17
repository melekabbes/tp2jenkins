pipeline {
    agent any

    tools {
        maven 'maven'
    }

    stages {
        stage("Clean up") {
            steps {
                deleteDir()
            }
        }

        stage("Clone repo") {
            steps {
                git url: 'https://github.com/melekabbes/tp2jenkins.git'
            }
        }

        stage("Generate backend image") {
            steps {
                bat "mvn clean install"
                bat "docker build -t tp2jenk:%BUILD_NUMBER% ."
            }
        }

        stage("Run docker compose") {
            steps {
                bat "docker-compose up -d"
            }
        }
    }
}
