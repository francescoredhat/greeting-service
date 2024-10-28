pipeline{
    agent{
        label "nodejs"
    }
    stages{
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                 
                sh "eslint . --ext .js,.jsx,.ts,.tsx"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }

        stage('Deploy') {
            steps {
               sh '''
                 oc project cmfrmz-greetings
                 oc start-build greeting-service --follow --wait
               '''
            }
        }
    }
}
