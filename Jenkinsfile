node{

    stage('Hello'){
        echo "hello World"
        
    }
    stage('continuesDownload'){
        git 'https://github.com/Technicalcourses2021/webapp1.git'
    }
    stage('continuousBuild'){
       withMaven(maven: 'M2_HOME') {
           sh 'mvn clean install package'
    }
        
    }
    stage('continuousDeployment'){
        deploy adapters: [tomcat8(credentialsId: 'tomcat-deployment', path: '', url: 'http://172.31.94.84:8090')], contextPath: null, war: '**/*.war'
    }
}
