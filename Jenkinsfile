// Jenkinsfile (Declarative Pipeline)
// node {
//     // checkout scm 
//     /* .. snip .. */
// }
// pipeline {
//     environment {
//         imagename = "kdk411/jenkins_demo"
//         registryCredentialsId "donnie_docker_hub"
//         dockerImage = 'tester'
//     }

//     agent any

//     stages {

//         stage('Cloning Git') {
//             steps {
//                 git([url: 'https://github.com/ismailyenigul/hacicenkins.git', branch: 'master', credentialsId: 'ismailyenigul-github-user-token'])
//             }
//         }

//         stage('Building image') {
//             steps{
//                 script {
//                     dockerImage = docker.build imagename
//                 }
//             }
//         }

//         stage('Deploy Image') {
//             steps{
//                 script {
//                     docker.withRegistry( '', registryCredential ) {
//                         dockerImage.push("$BUILD_NUMBER")
//                         dockerImage.push('latest')

//                     }
//                 }
//             }
//         }

//         stage('Remove Unused docker image') {
//             steps{
//                 sh "docker rmi $imagename:$BUILD_NUMBER"
//                 sh "docker rmi $imagename:latest"

//             }
//         }
//     }
// }


pipeline {
    agent any
    stages {
        stage('base-build') {
            environment {
                DOCKER_BUILDKIT="1"
            }
            agent { 
                dockerfile {
                    filename "Dockerfile.dummy"
                    dir "."
                    // label "tester:${env.BUILD_TAG}"
                    registryUrl "https://hub.docker.com/r/kdk411/jenkins_demo"
                    
                }
            }
            steps {
                echo 'Building ..'
            }
        }
        stage('base-test') {
            steps {
                sh "pip list | grep psutil"
            }
        }
    }
}