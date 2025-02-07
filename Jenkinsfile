pipeline {
    agent any

    environment {
        JAVA_VERSION = "17"
        JAVA_HOME = "/usr/lib/jvm/java-17-openjdk-amd64"
        PATH = "$JAVA_HOME/bin:$PATH"
    }

    stages {
        stage('Install Java 17') {
            steps {
                script {
                    sh '''
                    echo "Installing Java 17..."
                    sudo apt update
                    sudo apt install -y openjdk-17-jdk
                    echo "export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64" >> $HOME/.bashrc
                    echo "export PATH=$JAVA_HOME/bin:$PATH" >> $HOME/.bashrc
                    source $HOME/.bashrc
                    java -version
                    '''
                }
            }
        }
    }
}
