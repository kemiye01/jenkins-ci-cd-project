pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                echo 'Building..'
		sh '/usr/share/maven/bin/mvn package'
            }
        }
        stage('test') {
            steps {
                echo 'Building..'
		sh '/usr/share/maven/bin/mvn test'
            }
        }
       stage('deploy') {
    steps {
        echo 'Deploying....'
        sshagent(['Deploy_user']) {
            sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/jenkins-pipe/target/webapp-0.2.war centos@34.204.81.188:/home/centos"
        }
    }
}
