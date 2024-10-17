pipeline {
    agent any 

    triggers {
        cron('H/10 * * * 1') 
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh './mvnw clean package'
                }
            }
        }
        stage('Code Coverage') {
            steps {
                script {
                    sh './mvnw jacoco:report'
                }
            }
        }
    }

    post {
        always {
            jacoco execPattern: 'target/jacoco.exec', classPattern: 'target/classes', sourcePattern: 'src/main/java', inclusionPattern: '**/*.class'
        }
    }
}
