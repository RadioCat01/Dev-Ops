pipeline {
    agent any

    tools {
        jdk 'JDK17'         // Make sure JDK17 is configured in Jenkins
        maven 'Maven3'      // Same for Maven
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
                        // Kill any previous running instance
                        sh "pkill -f 'java -jar' || true"
                        // Run new JAR in background
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

