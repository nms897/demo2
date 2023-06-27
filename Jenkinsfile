pipeline{
    agent any
    tools {
  maven 'm1'
}
stages {
  stage('clone') {
    steps {
      checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'nms897', url: 'https://github.com/nms897/demo2.git']])
    }
  }
  stage('build') {
    steps {
      sh 'mvn clean install'
    }
  }

  stage('test') {
    steps {
      sh 'mvn test'
    }

    post {
      always {
        archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
              }
    }
  }
}
}
