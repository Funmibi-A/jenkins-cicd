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
                    hostname
                    whoami
                    ls -l /usr/bin/python3
                    /usr/bin/python3 --version
                    /usr/bin/python3 -m venv .venv
                    .venv/bin/python -m pip install --upgrade pip
                    .venv/bin/python -m pip install -r requirements.txt
                    .venv/bin/python -m compileall -q app.py tests
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
