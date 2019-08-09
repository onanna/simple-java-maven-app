pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
    node {
        checkout([
                         $class: 'GitSCM',
                         branches: scm.branches,
                         doGenerateSubmoduleConfigurations: scm.doGenerateSubmoduleConfigurations,
                         extensions: scm.extensions,
                         userRemoteConfigs: scm.userRemoteConfigs
                    ])
    }
}