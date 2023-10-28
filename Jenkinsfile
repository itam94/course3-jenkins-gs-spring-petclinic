pipeline {
    agent any
    stages{
        stage("Build"){
            steps{
                bat "./mvnw.cmd package"
            }
        }
    
        stage("capture"){
            steps{
                archiveArtifacts '**/target/*.jar'
                junit '**/target/surefire-reports/TEST*.xml'
                jacoco()
            }
        }
    }
    
    post{
        always{
            echo"${currentBuild.currentResult}: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}"
        }
    }
}