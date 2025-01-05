pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                echo "Clone the Repository"
            }
        }
        stage('Build Application') {
            steps {
                echo 'Build Application'
            }
        }
        stage('Package Application') {
            steps {
                echo 'Package Application'
            }
        }
        stage('Upload to JFrog Artifactory') {
            steps {
                rtServer (
                    id: 'Artifactory-Server',
                    url: 'https://triald4bgge.jfrog.io/artifactory/test-Website/',
                    credentialsId: 'Jfrog'
                )
                rtUpload (
                    serverId: 'Artifactory-Server',
                    spec: '''{
                        "files": [
                            {
                        "pattern": "index.html",
                        "target": "web-static-files/"
                    },
                                                {
                        "pattern": "styles.css",
                        "target": "web-static-files/"
                    }
                        ]
                    }'''
                )
        }
    }
    }
}
