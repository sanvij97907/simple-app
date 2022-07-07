pipeline {
    agent any
//     tools {
//         maven 'maven3'
//     }
//     options {
//         buildDiscarder logRotator(daysToKeepStr: '5', numToKeepStr: '7')
//     }
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
                 archiveArtifacts artifacts: 'target/*.war', onlyIfSuccessful: true
            }
        }
        stage('Upload War To Nexus'){
            steps{
        nexusArtifactUploader artifacts: [
            [
                artifactId: 'simple-app', 
                classifier: '', 
                file: 'targets/simple-app-3.0.0.war', 
                type: 'war'
                ]
                
                ],
                 credentialsId: 'accunoxwithnexus', 
                 groupId: 'in.javahome', 
                 nexusUrl: 'artifactory.accuknox.com',
                 
             nexusVersion: 'nexus3', 
             protocol: 'https', 
             repository: 'https://artifactory.accuknox.com/repository/simpleapp-release/', 
             version: '3.0.0' 
            }
        }
    }
}
