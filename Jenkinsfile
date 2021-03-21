pipeline {
  agent any
  stages {
    stage('Docker Build') {
      steps {
        sh "docker build -t ehab123/helloworld:${env.BUILD_NUMBER} application/"
      }
    }
    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker_registry_cred', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh "docker push ehab123/helloworld:${env.BUILD_NUMBER}"
        }
      }
    }
    stage('Docker Remove Image') {
      steps {
        sh "docker rmi ehab123/helloworld:${env.BUILD_NUMBER}"
      }
    }
}
post {
    success {
      echo "Pipeline is successfully completed."
    }
    failure {
      echo "Pipeline failed. Please check the logs."
    }
}
}
