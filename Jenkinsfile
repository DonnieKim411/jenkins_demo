Jenkinsfile (Declarative Pipeline)
node {
    // checkout scm 
    /* .. snip .. */
}
pipeline {
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
                    registryCredntialId "donnie_docker_hub"
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