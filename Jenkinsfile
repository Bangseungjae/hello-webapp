pipeline {
  agent { label 'jenkins-node' }

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
        sh 'scp /var/lib/jenkins/workspace/test/target/hello-world.war root@3.34.141.54:/var/lib/tomcat9/webapps'
      }
    }
  }
}
