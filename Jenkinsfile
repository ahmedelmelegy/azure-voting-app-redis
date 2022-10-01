pipeline {
    agent any
//     tools {
//         'org.jenkinsci.plugins.docker.commons.tools.DockerTool' 'docker'
//     }
    stages {
        stage('Verify Branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Docker Build') {
            steps {
                sh(script: 'docker images -a')
                sh(script: """
                    cd azure-vote/
                    sudo docker images -a
                    sudo docker build -t jenkins-pipeline .
                    sudo docker images -a
                    cd ..
                """)
            }
        }
    }
}
