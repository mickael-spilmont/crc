pipeline {
    agent {
      docker {
        image 'coverage:1.0'
        args '-v $WORKSPACE/:/code'
      }
    }
    stages {
        stage('build') {
            steps {
              echo "############################################################"
              echo "#                        BUILD                             #"
              echo "############################################################"
              sh "sh init_build.sh"
            }
        }
        stage('test') {
            steps {
              echo "############################################################"
              echo "#                        test                              #"
              echo "############################################################"
              sh "sh init_test.sh"
            }
        }
        stage('coverage') {
            steps {
              echo "############################################################"
              echo "#                      COVERAG                             #"
              echo "############################################################"
              sh "sh init_coverage.sh"
            }
        }
    }
    post {
        always {
            publishHTML([allowMissing: false,
              alwaysLinkToLastBuild: false,
              keepAll: true,
              reportDir: 'build/coverage/',
              reportFiles: 'index.html',
              reportName: 'HTML Report',
              reportTitles: ''
            ])
        }
    }
}
