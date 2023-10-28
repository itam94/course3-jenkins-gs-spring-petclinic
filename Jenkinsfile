pipeline {
    agent any
    stages{
        stage("Checkout"){
            steps{
                git branch:'main', url:'https://github.com/itam94/course3-jenkins-gs-spring-petclinic'
            }
        }
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