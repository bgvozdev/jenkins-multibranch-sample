pipeline {
    agent  any
    stages {
        stage('build') {
            steps {
                echo  'done build'
            }
        }
       stage('deploy') {
           steps {
            echo 'done deployment'
            exit 1
           }
      }
    }
}