pipeline {
    agent any

    stages {
        stage('Compile') {
          steps {
            // Compile the app and its dependencies
            echo "Compile stage passed"
          }
        }
        stage('Test') {
            steps {
                echo "Test stage passed"
            }
        }
        stage('Build') {
            steps {
                fastlane gym
                archiveArtifacts '**/*.ipa'
                echo "Build stage passed"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }

    environment {
                EMAIL_TO = 'satnam.malhotra@3pillarglobal.com'
    }

    post{
        always{
         // Cleaning workspace
         deleteDir()
        }
        success{
            echo env.BUILD_NUMBER
            mail to: EMAIL_TO, from: 'Jenkins_Build',
            subject: 'Build passed in Jenkins:',
            body: 'Check console output'
        }
        failure{
           echo env.BUILD_NUMBER
           mail to: EMAIL_TO, from: 'Jenkins_Build',
           subject: 'Build failed in Jenkins:',
           body: 'Check console output'
       }

    }
}