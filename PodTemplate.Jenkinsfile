podTemplate(
    agentContainer: 'jnlp',
    agentInjection: true,
    containers: [
        containerTemplate(
            name: 'docker',
            image: 'docker:latest',
            ttyEnabled: true,
            command: 'cat',
            volumeMounts: [
                volumeMount(
                    name: 'docker-sock',
                    mountPath: '/var/run/docker.sock'
                )
            ]
        ),
        containerTemplate(
            name: 'jnlp',
            image: 'registry.redhat.io/ocp-tools-4/jenkins-agent-base-rhel8:v4.15.0-1730196763',
            ttyEnabled: true,
            args: '$(JENKINS_SECRET) $(JENKINS_NAME)'
        )
    ],
    volumes: [
        persistentVolumeClaim(
            claimName: 'docker-sock',
            mountPath: '/var/run/docker.sock',
            readOnly: false
        )
    ]
) {
    node(POD_LABEL) {
        stage('Docker') {
            steps {
                container('docker') {
                    sh 'docker --version'
                }
            }
        }
    }
}