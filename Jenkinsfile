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
                    sh 'sudo usermod -a -G docker jenkins'
                    sh 'docker pull busybox:uclibc'
                }
            }
        }
    }
}
