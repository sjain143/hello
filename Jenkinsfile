pipeline{
    agent any
    stages{
        stage('Sumit'){
            
        
            steps{
                echo "executed"
                //input('do u wnat to proeceed')
                //checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/msoni103/hello.git']]])
                $git status
               // bat "\"${tool 'msbuild'}\" hello /p:Configuration=Debug /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
            }
        }   
        stage('testing') {
            
            steps{
                echo "emailing "
                mail bcc: '', body: 'testing', cc: '', from: '', replyTo: '', subject: 'hello', to: 'manish_soni@optum.com'
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
