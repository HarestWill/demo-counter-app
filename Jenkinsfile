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

        // stage("Integration testing"){

        //     steps{
        //         sh 'mvn verify -DskipUnitTests'
        //     }
        // }

        // stage('Maven Build'){

        //     steps{
        //         sh 'mvn clean install'
        //     }
        // }

        // stage('Maven Test'){

        //     steps{
        //         sh 'mvn test'
        //     }
        // }

        // stage('Checkstyle Analysis'){

        //     steps{
        //         sh 'mvn checkstyle:checkstyle'
        //     }
        // }

        // stage('SonarQube analysis'){

        //     steps{
        //         script{
        //             withSonarQubeEnv(credentialsId: 'MySonarToken') {
        //             sh 'mvn clean package sonar:sonar'
        //         }
        //         }
        //     }
        // }

        // stage('Quality Gates'){

        //     steps{
        //         script{
        //             waitForQualityGate abortPipeline: false, credentialsId: 'MySonarToken'
        //         }
        //     }
        // }

        // stage('Upload jar file to Nexus'){

        //     steps{
        //         script{
        //             def readPomVersion = readMavenPom file: 'pom.xml'

        //             def nexusRepo = readPomVersion.version.endsWith("SNAPSHOT") ? "demoapp-snapshot" : "demoapp-release"
        //             nexusArtifactUploader artifacts: [
        //                 [
        //                     artifactId: 'springboot', 
        //                     classifier: '', file: 'target/Uber.jar', 
        //                     type: 'jar'
        //                     ]
        //                     ], 
        //                     credentialsId: 'nexus-auth', 
        //                     groupId: 'com.example', 
        //                     nexusUrl: '3.231.219.97:8081', 
        //                     nexusVersion: 'nexus3', 
        //                     protocol: 'http', 
        //                     repository: nexusRepo, 
        //                     version: "${readPomVersion.version}"
        //         }
        //     }
        // }

        // stage('Docker Image build'){

        //     steps{

        //         script {
        //             sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID .'
        //             sh 'docker image tag $JOB_NAME:v1.$BUILD_ID harest/$JOB_NAME:v1.$BUILD_ID'
        //             sh 'docker image tag $JOB_NAME:v1.$BUILD_ID harest/$JOB_NAME:latest'

        //         }
        //     }
        // }

        // stage('Push Image to DockerHub'){

        //     steps{

        //         script{
        //             withCredentials([string(credentialsId: 'git_cred', variable: 'docker_hub_cred')]) {

        //                 sh 'docker login -u harest -p ${docker_hub_cred}'
        //                 sh 'docker image push harest/$JOB_NAME:v1.$BUILD_ID'
        //                 sh 'docker image push harest/$JOB_NAME:latest'
 
        //                 }
        //             }
        //         }
        //     }
        }
    }