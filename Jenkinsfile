pipeline {
    agent any

    environment {
        MAVEN_VERSION = '3.9.9'
        MAVEN_HOME = "/opt/apache-maven-${MAVEN_VERSION}"
        PATH = "$MAVEN_HOME/bin:$PATH"
    }

    stages {
        stage('Setup Maven') {
            steps {
                script {
                    if (!fileExists(MAVEN_HOME)) {
                        error("Error: Maven directory ${MAVEN_HOME} not found. Please ensure it is installed.")
                    }
                }
                sh 'mvn -version'
            }
        }

        stage('Clean') {
            steps {
                sh 'mvn clean'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mvn deploy'
            }
        }
    }
}
