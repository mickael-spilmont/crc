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
                sh "gcc --version"
            }
        }
    }
}
