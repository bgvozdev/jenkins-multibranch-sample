pipeline {
    agent  any
    stages {
        stage('build') {
            steps {
                sleep 20
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
