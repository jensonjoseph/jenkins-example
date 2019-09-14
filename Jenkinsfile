pipeline {
    agent any
    tools {
        maven 'maven_3_3_9'
    }

    stages {

        if(true) {
            stage ('Restart') {

                        steps {
                            sh 'mvn clean compile'
                        }
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