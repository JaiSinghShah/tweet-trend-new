pipeline {
    agent {
        node {
            label 'maven'

        }
    }  
environment {
    PATH = "/opt/apache-maven-3.9.9/bin:$PATH"
}   
    stages {
        stage("build"){
            steps {
                sh 'mvn clean deploy'
            }
        }
        
    }
}
:q
[A[3~[3~[C
[A[A