pipeline {
  agent any
  stages {
    stage('scm checkout') {
      steps {
        git branch: 'master', url: 'https://github.com/shailesh2529/maven-project.git'
      }
    }

    stage('compile the job') //validate then compile
    {
      steps {
        withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn compile'
        }
      }
    }
    stage('build the code') {
      steps {
        withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn clean package'
        }
      }
    }

    stage('create docker image') {
      steps {
        sh 'docker build -t shaileshpa/ethans954-dockerhubfinal:latest .'
      }
    }

    stage('push docker image to dockerhub') {
      steps {
        
        withDockerRegistry(credentialsId: 'DockerHubCredentials', url: 'https://index.docker.io/v1/') {
            
                sh 'docker push shaileshpa/ethans954-dockerhubfinal:latest'
            
        }
      }
    }
  }
}
