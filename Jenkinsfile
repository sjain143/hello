pipeline{
    agent any
    stages{
        stage('compile'){
            
            steps{
                echo "executed"
                input('do u wnat to proeceed')
               
            }
        }   
        stage('testing') {
            
            steps{
                echo "testing"
            }
        }
        
        stage('deploy'){
            parallel{
                stage('unit test'){
                    steps{
                        echo 'running unit test'
                    }
                }
                stage('integrationtest'){
                    steps{
                        echo 'running integration test'
                    }
                }
            }
        }
        
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
