pipeline{
    agent any
    parameters{
        string(name:'BRANCH_NAME',defaultValue:'master',description:'default branch name')
    }
    stages{
        stage('checkout'){
            steps{git branch:params.BRANCH_NAME, url:https://github.com/anishudupan-rns/devops-pgrm9.git}
        } 
        stage("Build"){
            steps{ sh 'mvn clean package'}
        }
        stage("Test"){
            steps{sh 'mvn test'}
        }
    }
    post{
        success{
            archiveArtifacts artifacts: 'target/*.jar',fingerprint:true
        }
    }
}
