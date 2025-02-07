pipeline {
    agent any

    environment {
        MAVEN_VERSION = '3.9.9'
        MAVEN_HOME = "/opt/apache-maven-${MAVEN_VERSION}"
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk'
        PATH = "$JAVA_HOME/bin:$MAVEN_HOME/bin:$PATH"
    }

 stage('Install Java 17') {
     steps {
        script {
            sh '''
            sudo apt update
            sudo apt install -y openjdk-17-jdk
            echo "export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64" >> $HOME/.bashrc
            echo "export PATH=$JAVA_HOME/bin:$PATH" >> $HOME/.bashrc
            source $HOME/.bashrc
            java -version
            '''
            
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
