pipeline {
    agent  any
    stages {
        stage('build') {
            steps {
                echo  'done build'
            }
        }
        stage('Request approval') { // Raise change request
            steps {
                echo 'Raise change request...'
                jiraSendDeploymentInfo(site:'bgvozdev-testing-gating.atlassian.net',
                        environmentId:'us-prod-1',
                        environmentName:'us-prod-1',
                        environmentType:'production',
                        state:"pending",
                        enableGating:true, 
                        serviceIds: [
                          'b:YXJpOmNsb3VkOmdyYXBoOjpzZXJ2aWNlLzE1MTIwNzk0LWZiYTItNDFjNy04M2RhLWE1NWY2ZDU0N2ZmMi9jYzlkZDQxMC1hNWE5LTExZWMtYjM1OS0wZTNlN2EyMWE5MTE='
                        ]
                    )
            }
          } 
        stage("Approval gate") { 
            steps {
                  waitUntil {
                      sleep 5
                      checkGatingStatus(
                        site:'bgvozdev-testing-gating.atlassian.net', 
                        environmentId:'us-prod-1'
                      )
                  }
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
