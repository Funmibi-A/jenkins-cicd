pipeline {
    agent any

    options {
        timestamps()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh '''
                    echo "=== Jenkins execution environment ==="
                    whoami
                    hostname
                    echo "PATH=$PATH"
                    command -v python3 || true
                    ls -l /usr/bin/python3 || true
                    /usr/bin/python3 --version || true
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    .venv/bin/python -m pytest -v \
                        --junitxml=test-results.xml
                '''
            }

            post {
                always {
                    junit allowEmptyResults: true,
                          testResults: 'test-results.xml'
                }
            }
        }

        stage('Package') {
            steps {
                sh '''
                    mkdir -p dist
                    zip -r dist/jenkins-cicd-${BUILD_NUMBER}.zip \
                        app.py requirements.txt tests \
                        -x '*__pycache__*' '*.pyc'
                '''
                archiveArtifacts artifacts: 'dist/*.zip',
                                 fingerprint: true
            }
        }
    }
}
