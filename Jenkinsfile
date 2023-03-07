pipeline {
  agent { label 'jenkins-node' }

  triggers {
  pollSCM '* * * * *'
  }
  
  parameters {
  string defaultValue: '3.34.141.54', name: 'TOMCAT_IP'
  string defaultValue: '/var/lib/tomcat9/webapps', name: 'TOMCAT_WEBAPP_DIR'
  }
  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/Bangseungjae/hello-webapp.git'
      }
    }

    stage('Maven Build') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('Deploy to Tomcat') {
      steps {
        sh 'scp ${env.WORKSPACE}/target/hello-world.war root@${params.TOMCAT_IP}:${params.TOMCAT_WEBAPP_DIR}'
      }
    }
  }
}
