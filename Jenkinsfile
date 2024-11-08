pipeline {
    agent any

    environment {
        SCANNER_HOME = tool 'sonar-scanner'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', credentialsId: 'git-cred', url: 'https://github.com/KhaledGs5/trello-clone-static-code-analysis.git'
            }
        }
        stage('Sonarqube Analysis') {
            steps {
                sh """
                ${SCANNER_HOME}/bin/sonar-scanner \
                -Dsonar.host.url=http://localhost:9000 \
                -Dsonar.login=squ_a4bc5f41b84443c6b8aa8f5453c7775407e4647b \
                -Dsonar.projectName=Trello \
                -Dsonar.java.binaries=. \
                -Dsonar.projectKey=Trello \
                -X
                """
            }
        }
        // stage('OWASP SCAN') {
        //     steps {
        //         dependencyCheck additionalArguments: ' --scan ./', odcInstallation: 'DP'
        //         dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
        //     }
        // }
        // stage('Docker Build and Push') {
        //     steps {
        //         script {
        //             withDockerRegistry(credentialsId: 'docker-cred') {
        //                 sh "docker build -t khaledgs/fixprostho ."
        //                 sh "docker push khaledgs/fixprostho"
        //             }
        //         }
        //     }
        // }
    }
}

