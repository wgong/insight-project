pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '''
                    echo "upload Lambda function"
                    ## ./upload-lambda-xml.sh
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'echo "run integration test"'
                sh '''
                    source ~/.aws/env_var
                    echo ${AWS_S3_BUCKET}
                    echo ${AWS_PG_DB_HOST}
                    echo "activate py3"
                    source ~/py36/bin/activate
                    which python3
                    which pytest
                    echo "run pytest"
                    cd src/lambda_xml
                    pytest -q test_lambda_function_xml.py
                '''
            }
        }
    }
}

