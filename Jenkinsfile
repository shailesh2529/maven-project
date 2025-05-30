pipeline {
    agent any
    stages {
        stage('scm checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/shailesh2529/maven-project.git'
            }
        }

        stage('code validate')
        {
            steps {
                   withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn validate'//+validate
                }

                stage('code compile')
        {
            steps {
                   withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn compile'//+validate+compile
                }

                stage('code test')
        {
            steps {
                   withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn test'//+validate+compile+test
                }

        stage('code build')
        {
            steps {
                   withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn package'//+validate+compile+test+package
                }
            }
        }


        stage('code deploy') //will deploy on target machine
        {
            steps {

                  Sh ‘Scp /var/lib/jenkins/workspace/p1/webapp/target/webapp.war ec2-user@18.61.44.180:/usr/share/tomcat/webapps’
    }
}
