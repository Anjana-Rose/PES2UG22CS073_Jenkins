pipeline {
    agent any

    environment {
        CXX = 'g++'  
        FILE_NAME = 'teatime.cpp'
        EXEC_FILE = 'teatime.out'
        REPO_URL = 'https://github.com/Anjana-Rose/PES2UG22CS073_Jenkins.git' 
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    echo "Cloning the repository..."
                    checkout([$class: 'GitSCM',
                        branches: [[name: '*/main']], 
                        userRemoteConfigs: [[url: "$REPO_URL"]]  
                    ])
                }
            }
        }

        stage('Build') {
            steps {
                script {

                    build 'PES2UG22CS073-1' 
                    echo "Compiling the C++ file..."
                    sh '''
                    g++ $FILE_NAME -o $EXEC_FILE
                    '''
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo "Testing the C++ file..."
                    sh '.' + EXEC_FILE
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo "Deploying the application..."
                }
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
        success {
            echo 'Pipeline succeeded'
        }
    }
}
