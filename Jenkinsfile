pipeline {
    agent any

    stages {
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_2pbRSykxKBImSXToCai7qONAxxA | /usr/local/bin/docker login -u akshayrajodiya--password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/local/bin/docker build -t akshayrajodiya/my_jen_pip .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/local/bin/docker image push akshayrajodiya/my_jen_pip'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/local/bin/docker service rm jenpipeservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/local/bin/docker service create --name jenpipeservice --replicas 5 -p 9876:80 jenpipeservice'
            }
        }
    }
}