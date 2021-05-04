node {
    docker.withRegistry('https://hub.docker.com/repository/docker/kdk411/jenkins_demo', 
                        'docker_hub_credentials') {

        stage("docker-build"){
                def dockerfile = 'Dockerfile.dummy'
                def customImage = docker.build("my-image:${env.BUILD_ID}", "-f ${dockerfile} .") 
            }

        stage("docker-test"){
            customImage.inside {sh "pip list | grep psutil"}
        }
    }
}



// node {
//     def mvnHome
//     stage('Preparation') { // for display purposes
//         // Get some code from a GitHub repository
//         git 'https://github.com/jglick/simple-maven-project-with-tests.git'
//         // Get the Maven tool.
//         // ** NOTE: This 'M3' Maven tool must be configured
//         // **       in the global configuration.
//         mvnHome = tool 'M3'
//     }
//     stage('Build') {
//         // Run the maven build
//         withEnv(["MVN_HOME=$mvnHome"]) {
//             if (isUnix()) {
//                 sh '"$MVN_HOME/bin/mvn" -Dmaven.test.failure.ignore clean package'
//             } else {
//                 bat(/"%MVN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean package/)
//             }
//         }
//     }
//     stage('Results') {
//         junit '**/target/surefire-reports/TEST-*.xml'
//         archiveArtifacts 'target/*.jar'
//     }
// }



// {
//     node {
//         checkout scm
        
//     }
// }




// // Jenkinsfile (Declarative Pipeline)
// // node {
// //     // checkout scm 
// //     /* .. snip .. */
// // }
// // pipeline {
// //     environment {
// //         imagename = "kdk411/jenkins_demo"
// //         registryCredentialsId "donnie_docker_hub"
// //         dockerImage = 'tester'
// //     }

// //     agent any

// //     stages {

// //         stage('Cloning Git') {
// //             steps {
// //                 git([url: 'https://github.com/ismailyenigul/hacicenkins.git', branch: 'master', credentialsId: 'ismailyenigul-github-user-token'])
// //             }
// //         }

// //         stage('Building image') {
// //             steps{
// //                 script {
// //                     dockerImage = docker.build imagename
// //                 }
// //             }
// //         }

// //         stage('Deploy Image') {
// //             steps{
// //                 script {
// //                     docker.withRegistry( '', registryCredential ) {
// //                         dockerImage.push("$BUILD_NUMBER")
// //                         dockerImage.push('latest')

// //                     }
// //                 }
// //             }
// //         }

// //         stage('Remove Unused docker image') {
// //             steps{
// //                 sh "docker rmi $imagename:$BUILD_NUMBER"
// //                 sh "docker rmi $imagename:latest"

// //             }
// //         }
// //     }
// // }


// pipeline {
//     agent any
//     stages {
//         stage('base-build') {
//             environment {
//                 DOCKER_BUILDKIT="1"
//             }
//             agent { 
//                 dockerfile {
//                     filename "Dockerfile.dummy"
//                     dir "."
//                     // label "tester:${env.BUILD_TAG}"
//                     registryUrl "https://hub.docker.com/r/kdk411/jenkins_demo"
                    
//                 }
//             }
//             steps {
//                 echo 'Building base-build'
//             }
//         }
//         // stage('base-test') {
//         //     steps {
//         //         sh "pip list | grep psutil"
//         //     }
//         // }
//     }
// }