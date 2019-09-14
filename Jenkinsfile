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

            steps {
                sh 'mvn clean compile'
            }
        }

        stage ('Testing Stage') {

            steps {
                sh 'mvn test'
            }
        }

        stage ('Deployment Stage') {
            steps {
                sh 'mvn deploy'
            }
        }
    }
}