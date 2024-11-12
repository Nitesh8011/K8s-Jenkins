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
                    sh 'docker pull busybox:uclibc'
                }
            }
        }
    }
}
