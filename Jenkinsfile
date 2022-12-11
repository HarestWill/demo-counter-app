pipeline{

    agent any

    stages{

        stage("Git Checkout"){

            steps{
                git branch: 'main', url: 'https://github.com/HarestWill/demo-counter-app.git'
            }
        }

        stage("UNIT Testing"){

            steps{
                sh 'mvn test'
            }
        }

        stage("Integration testing"){

            steps{
                sh 'mvn verify -DskipUnitTests'
            }
        }

        stage('Maven Build'){

            steps{
                sh 'mvn clean install'
            }
        }

        stage('Maven Test'){

            steps{
                sh 'mvn test'
            }
        }

        stage('Checkstyle Analysis'){

            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }

        stage('Static code analysis'){

            steps{
                withSonarQubeEnv(credentialsId: 'MySonarToken') {
                    sh 'mvn clean package sonar:sonar'
                }
}
            }
        }
    }

}