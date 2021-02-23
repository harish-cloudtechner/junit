pipeline {
            agent any
            tools {
                maven 'maven'
                }
            stages {
                stage('Git Checkout') {
                     steps {
                         git branch: 'main',
                         credentialsId: 'abaf8590-6021-4c4a-8ee7-8b43d17460ee',
                         url: 'https://github.com/hsct2707/jenkins.git'
                         }
                      }
               stage ('Compile') {
                    steps {
                        sh 'mvn compile'
                       }
                    }
               stage('Test') {
                   steps {
                       sh 'mvn test'
                      }
              post {
                  always {
                       junit 'target/pom/*.xml'
                      }
                   }
              }
                  stage('Deliver') {
                      steps {
                          sh './jenkins/scripts/deliver.sh'
                      }
                }
          }
      }
