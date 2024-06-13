pipeline {
    agent any
    stages {
        stage ('Clean'){
            steps {
                cleanWs()
                git url: 'https://github.com/oluwaseyiaduloju/jenkins-freestyle-project', branch: 'main'
            }
        }
        stage ('Run script'){
            steps {
                sh "run.sh"
            }
        }
        stage ('Generate artifacts'){
            sh '''
            #!/bin/bash
            for i in {1..5}; do echo "This is file \$i" > file\$i.txt; done
            '''
        }
        post {
            always{
                archiveArtifacts artifacts: '*.txt', followSymlinks: false
            }
        }
    }
}