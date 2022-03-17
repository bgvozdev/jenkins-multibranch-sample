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
                          'b:YXJpOmNsb3VkOmdyYXBoOjpzZXJ2aWNlLzdkYzU4ODQ2LTYzZDUtNGMwYS05YTYyLWJiYTBiYTVlNjEwYS9lOGQwMTAwMi1hNWFhLTExZWMtYjJiZC0wYWJlM2Y0YTY2MDE='
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
