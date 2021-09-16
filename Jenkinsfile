pipeline {
    agent any
    tools {
      maven 'M2_HOME'
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Continuesdownload'){
            steps {
                git 'https://github.com/Technicalcourses2021/webapp1.git'
            }
        }
        stage('ContinuesBuild'){
            steps{
                sh 'mvn clean install package'
            }
            
        }
        stage('ContinuesDeployment'){
            steps{
                deploy adapters: [tomcat8(credentialsId: 'tomcat-deployment', path: '', url: 'http://172.31.94.84:8090')], contextPath: null, war: '**/*.war'
            }
            
        }
        stage('continuesTesting'){
            steps{
                git branch: 'main', credentialsId: 'GitHUbPWD', url: 'https://github.com/Technicalcourses2021/sampleMavenJunit.git'
                sh 'mvn clean install'
            }
            
        }
        
    }
}
