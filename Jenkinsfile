pipeline {
    agent any

    environment {
        MAVEN_VERSION = '3.9.9'
        MAVEN_HOME = "/opt/apache-maven-${MAVEN_VERSION}"
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk'
        PATH = "$JAVA_HOME/bin:$MAVEN_HOME/bin:$PATH"
    }

    stages {
        stage('Setup Environment') {
            steps {
                script {
                    if (!fileExists(MAVEN_HOME)) {
                        error("Error: Maven directory ${MAVEN_HOME} not found. Please ensure it is installed.")
                    }
                    if (!fileExists(JAVA_HOME)) {
                        error("Error: Java directory ${JAVA_HOME} not found. Please ensure Java 17 is installed.")
                    }
                }
                sh 'java -version'
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
