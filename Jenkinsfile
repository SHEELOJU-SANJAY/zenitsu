pipeline {
    agent none

    stages {
        stage('Run on Controller') {
            agent { label 'built-in' }
            steps {
                echo "Running on: built-in"
            }
        }

        stage('Run on Windows Agent') {
            agent { label 'Tejaswini' }
            steps {
                echo "Running on Windows Agent"
                bat '''
                    echo Running on Windows Agent
                    mkdir out
                    javac -d out src\\HelloWorld.java
                    java -cp out HelloWorld
                '''
            }
        }

        stage('Run in Parallel') {
            parallel {
                stage('Controller') {
                    agent { label 'built-in' }
                    steps {
                        echo "Controller Stage"
                    }
                }
                stage('Windows Agent') {
                    agent { label 'Tejaswini' }
                    steps {
                        echo "Windows Agent Stage"
                    }
                }
            }
        }
    }
}
