pipeline {

agent {
    node {
      label 'demoagent'
    }
  }
  
      tools {
        jdk 'java-8.221'
        maven 'maven-3.8.1'
    }
    
    stages {
        
     stage('Maven version test') {
            steps {
                echo "Hello, Maven"
                sh "mvn --version" 
            }
        }
        
        stage('Sonarqube') {
            environment {
                scannerHome = tool 'SonarQube-4.6.2'
            }
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
                timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }      

        stage('Stage 1') {
            steps {
                sh 'mvn clean package'
            }
            
        }
        
        stage('Stage 2') {
            steps {
                echo 'Stage2 Hello world!'  
                echo  'Stage2 $date'
               
            }
            
        }
        
        
        stage('Stage 3') {
            steps {
                echo 'Wel come to Stage3 '  
                echo  'Stage3 '
            }
            
        }           
    }
}
