pipeline {
  agent { label 'jenkins-node' }
  parameters {
    String(name: 'TOMCAT', defaultValue: '3.34.141.54', description: 'tomcat server ip')
    String(name: 'WORKDIR', defaultValue: '/var/lib/jenkins/workspace/test', description: 'working directory')
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
        sh 'scp ${params.WORKDIR}/target/hello-world.war root@${params.TOMCAT}:/var/lib/tomcat9/webapps'
      }
    }
  }
}
