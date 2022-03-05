pipeline {
    agent none
    stages {
        stage('Angular Verification') {
            agent {
                label "windows-worker"
            }
            steps {
                bat "ng version"
            }
        }
        
        stage('Dependencies Installation') {
            agent {
                label "windows-worker"
            }
            steps {
                bat "npm install"
            }
        }
    

        stage ("Unit Testing") {
            agent {
                label "windows-worker"
            }
            steps {
                bat "ng config -g cli.warnings.versionMismatch false"
                bat "ng test"
                echo "test passed"
            }
        }

            
        stage('Build Execution') {
            agent {
                label "windows-worker"
            }
            steps {
                script {
                    bat "ng build"
                }
            }
        }
        
        stage('Deploy Application') {
            agent {
                label "windows-worker"
            }
            steps {
                script {
                    powershell "cp -r ./dist/ng-video-game-db/*.* C:/inetpub/wwwroot/jose/dev/"
                }
            }
        }
    }
}