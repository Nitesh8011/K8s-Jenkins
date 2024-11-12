pipeline {
    agent {
        kubernetes {
            defaultContainer 'maven'
            yamlFile 'PodTemplate.yml'
        }
    }
    stages {
        stage('Clone') {
            steps {
                container('docker') {
                    sh 'docker pull busybox:uclibc'
                }
            }
        }
    }
    post {
        always {
            container('docker') {
                sh 'docker --version'
            }
        }
    }
}
