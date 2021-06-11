pipeline {
    agent any

    stages {
            stage('Checkout') {
                steps {
                    git 'https://github.com/shivaswaroop40/jenkin_deploy.git'
                }
            }
            stage('Build') {
                steps {

                    // Run Maven on a Unix agent.
                    sh "mvn -Dmaven.test.failure.ignore=true clean package"

                    // To run Maven on a Windows agent, use
                    // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
            
        }
            stage('Deploy') {
                steps {
                    deploy adapters: [tomcat9(credentialsId: 'Tomcat', path: '', url: 'http://[2406:7400:73:b4b0:3e4d:41a3:8643:5bc8]')], contextPath: 'Tomcat_war.war', war: 'target/Tomcat_war.war'
                }
            }
    }
}
