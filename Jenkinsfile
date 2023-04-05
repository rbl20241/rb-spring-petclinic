pipeline {
    agent any

    // tools {
    //     // Install the Maven version configured as "M3" and add it to the path.
    //     maven "M3"
    // }
    triggers { pollSCM('* * * * *') }

    stages {
//         stage("Checkout") {
//             steps {
//                 git branch: 'master', url: 'https://github.com/rbl20241/rb-spring-petclinic.git'
//             }
//         }
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }

        }
    }
    post {
        always {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
        }
    }
}
