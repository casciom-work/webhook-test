pipeline {
    agent any
    
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }

        stage ('Build') {
            steps {
                withEnv(["JAVA_HOME=/usr/bin/", "PATH+MAVEN=${tool 'maven3'}/bin:${env.JAVA_HOME}/bin"]) {
                    sh "mvn --batch-mode -V -U -e install -DskipTests -Dsurefire.useFile=false"
                }
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
    }
}
