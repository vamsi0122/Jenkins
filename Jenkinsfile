pipeline {
    agent {node { label 'Agent-1'} }

    

    options {
        timeout(time: 1, unit: 'HOURS') 
    }

    environment{
        USER = 'vamsi'
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {
        stage('Build-1'){
            steps {
                echo "====++++building++++===="
                sh'''
                ls -ltr
                pwd
                echo 'Hello build'
                printenv
                '''
            }
        }

        stage( 'Test-2'){
            steps {
                sh'''
                  echo 'Testing the codes test cases'
                '''
            }
            
        }

        stage( 'Deploy-3'){
            steps{
                sh'''
                  echo 'Deploying  the build'
                '''
            }
            
        }

        stage( 'Password-4'){
            environment{
                AUTH = credentials('centos')
            }

            steps {
                sh 'printenv'
            }
        }

        stage('Params') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }

    }
    
}