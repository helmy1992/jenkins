@Library('shared-lib') _  
pipeline {
     agent any
    parameters {
        booleanParam(name:'test', defaultValue: true, description:'this paramater help you to know project name')
        choice(name: 'namespace', choices:['dev','prod','stage'], description: '' ) 
    }

    stages {
        stage('build') {
            steps {
                buildingImage()
            }
        }

         stage('builddocker') {
            steps {
                  buldingdocker()
            }
        }

        stage('test') {
            when {
                expression{
                    params.test== true 
                }
            }
            steps {
                testing()
            }
        }
        
        stage('deploy') {  
            steps {
               deployingImage()
            }
        }    
    }

     post {
        always { 
            echo 'job was triggered'
        }
        success {
            echo 'your app is deployed successfully'
        }
        failure {
            echo 'deploying failure'
        }
    }
}
