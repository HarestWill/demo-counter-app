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

        stage('SonarQube analysis'){

            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'MySonarToken') {
                    sh 'mvn clean package sonar:sonar'
                }
                }
            }
        }

        stage('Quality Gates'){

            steps{
                script{
                    waitForQualityGate abortPipeline: false, credentialsId: 'MySonarToken'
                }
            }
        }

        stage(Upload jar file to Nexus){

            steps{
                script{

                    nexusArtifactUploader artifacts: [
                        [
                            artifactId: 'springboot', 
                            classifier: '', file: 'target/Uber.jar', 
                            type: 'jar'
                            ]
                            ], 
                            credentialsId: 'nexus-auth', 
                            groupId: 'com.example', 
                            nexusUrl: '3.231.219.97:8081', 
                            nexusVersion: 'nexus3', 
                            protocol: 'http', 
                            repository: 'demoapp-release', 
                            version: '1.0.0'
                }
            }
        }
    }

}