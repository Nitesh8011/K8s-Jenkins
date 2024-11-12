pipeline {
    agent {
        kubernetes {
            defaultContainer 'docker'
            yamlFile 'PodTemplate.yml'
        }
    }
    stages {
        stage('Clone') {
            steps {
                container('docker') {
                    sh 'docker --version'
                    sh 'sudo chmod 777 /var/run/docker.sock'
                    sh 'docker pull busybox:uclibc'
                }
            }
        }
    }
}
