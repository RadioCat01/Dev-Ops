pipeline {
    agent { label 'agent-01'}

    tools {
        jdk 'JDK17'         
        maven 'Maven3'     
    }

    environment {
        BUILD_DIR = 'app/target'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/RadioCat01/Noter'
            }
        }

        stage('Build Spring Boot App') {
            steps {
                dir('app') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }

        stage('Run App') {
            steps {
                script {
                    def jarName = sh(script: "ls ${BUILD_DIR}/*.jar | grep -v 'original' || true", returnStdout: true).trim()
                    if (jarName) {
                        echo "Running app: ${jarName}"
                        sh "pkill -f 'java -jar' || true"
                        sh "nohup java -jar ${jarName} --server.port=8081 > app.log 2>&1 &"
                    } else {
                        error("JAR not found in ${BUILD_DIR}")
                    }
                }
            }
        }
    }

    post {
        success {
            echo '✅ Spring Boot backend built and deployed!'
        }
        failure {
            echo '❌ Build or run failed. Check the logs.'
        }
    }
}

