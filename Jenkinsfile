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
              sh "sh launchCompil.sh"
            }
        }
    }
    post {
        always {
            publishHTML([allowMissing: false,
              alwaysLinkToLastBuild: false,
              keepAll: true,
              reportDir: 'build/coverage/html',
              reportFiles: 'index.html',
              reportName: 'HTML Report',
              reportTitles: ''
            ])
        }
    }
}
