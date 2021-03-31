// Jenkinsfile (Declarative Pipeline)
// node {
//     // checkout scm 
//     /* .. snip .. */
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
                    label "tester:${env.BUILD_TAG}"
                    registryCredentialsId "donnie_docker_hub"
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