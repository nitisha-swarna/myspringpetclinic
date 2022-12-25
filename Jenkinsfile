pipeline {
    agent any
    parameters {
        string(name: 'MAVEN_GOAL', defaultValue: 'clean install', description: 'maven goal')

    }
    triggers {
        
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: "main", url: 'https://github.com/nitisha-swarna/myspringpetclinic.git'
            }
            
        }
 stage('Build the Code') {
            steps {
                
                    sh script: 'mvn clean install'
                
            }
        }
    }
}