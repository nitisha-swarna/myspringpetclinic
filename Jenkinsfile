pipeline {
    agent any
    triggers {
        cron('* 18 * * 1-5')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: "qa", url: 'https://github.com/nitisha-swarna/myspringpetclinic.git'
            }
            
        }
         stage ('Artifactory configuration') {
            steps {
                rtMavenDeployer (
                    id: "MAVEN_DEPLOYER",
                    serverId: "JFROG_OCT22",
                    releaseRepo: 'default-libs-release-local',
                    snapshotRepo: 'default-libs-snapshot-local'
                )
            }
        }
        stage ('Exec Maven') {
            steps {
                rtMavenRun (
                    tool: 'MAVEN_DEFAULT', // Tool name from Jenkins configuration
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: "MAVEN_DEPLOYER"
                )
            }
        }
    }
}
