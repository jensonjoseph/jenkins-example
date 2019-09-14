pipeline {
    agent any
    parameters {
        choice(
            choices: ['deploy' , 'restart'],
            description: 'Select either deploy or restart',
            name: 'REQUESTED_ACTION')
     }
    tools {
        maven 'maven_3_3_9'
    }

    stages {
        stage ('Restart') {
            when {
                expression { params.REQUESTED_ACTION == 'restart' }
            }
            steps {
                sh 'mvn clean compile'
                sh "exit 1"
            }
        }

        stage ('Compile Stage') {
            when {
                expression { params.REQUESTED_ACTION == 'deploy' }
            }
            steps {
                sh 'mvn clean compile'
            }
        }

        stage ('Testing Stage') {
            when {
                expression { params.REQUESTED_ACTION == 'deploy' }
            }
            steps {
                sh 'mvn test'
            }
        }

        stage ('Deployment Stage') {
            when {
                expression { params.REQUESTED_ACTION == 'deploy' }
            }
            steps {
                sh 'mvn deploy'
            }
        }
    }
}