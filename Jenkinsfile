pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '464f264c-738b-4ab7-98b9-7e3c187b98d3', url: 'git@github.com:tianyadaoke/jenkins-test-demo.git']]])
            }
        }
        stage('build code') {
            steps {
               bat 'mvn clean package'
            }
        }
        stage('publish code') {
            steps {
               deploy adapters: [tomcat9(credentialsId: 'd5d1b480-0cf9-438e-ba69-8d4dd6af0188', path: '', url: 'http://localhost:8080')], contextPath: null, war: 'target/*.war'
            }
        }
    }
}
