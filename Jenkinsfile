pipeline {
    agent any

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
                    apt-get update
                    apt-get install -y wget
                    wget https://download.docker.com/linux/static/stable/x86_64/docker-20.10.9.tgz
                    tar zxvf docker-20.10.9.tgz
                    cp -f docker/docker /usr/local/bin
                    rm -fr docker-20.10.0.tgz docker
                    apt-get purge -y wget
                    cd azure-vote/
                    docker images -a
                    docker build -t jenkins-pipeline .
                    docker images -a
                    cd ..
                """)
            }
        }
    }
}
