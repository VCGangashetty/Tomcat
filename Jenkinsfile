pipeline {    
    agent any

    tools {
        maven ('maven-3.9.2')
    }
  
    stages { 
        
        stage('BUILD-Maven') {
            
            steps { 
                sh '''
                   cd ./simple-war/
                   mvn clean package
                   cd ./target/
                   ls
                '''
                }
            }
        stage ('DEPLOY-Tomcat') {

            steps {
                script {
                  deploy adapters: [tomcat9(credentialsId: 'Tomcat-manager-credentials', path: '', url: 'http://3.110.29.144:8080/')], 
                  contextPath: '/itdefined-war-1.0.0', 
                  onFailure: false, 
                  war: 'simple-war/target/itdefined-war-1.0.0.war'
                }

            }
        }
    }
}