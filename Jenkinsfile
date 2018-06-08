pipeline {
    agent any
    
    tools { 
        maven 'm3' 
        jdk 'jdk10'
    }
    
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    echo "JAVA_HOME = ${JAVA_HOME}"
                    $JAVA_HOME/bin/java -v
                ''' 
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn install -DskipTests' 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
    }
}
