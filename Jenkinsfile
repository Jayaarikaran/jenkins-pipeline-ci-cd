pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Use Maven to build the project
                sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Use Maven for unit and integration tests
                sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis...'
                // Use SonarQube for code quality analysis
                sh 'mvn sonar:sonar'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Use OWASP ZAP for security scanning
                sh 'zap-baseline.py -t https://your-app.com'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
                // Deploy the app to a staging environment (e.g., AWS EC2)
                sh 'scp your-app.jar user@staging-server:/path'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Run integration tests in the staging environment
                sh './run_integration_tests.sh'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                // Deploy the app to the production environment (e.g., AWS EC2)
                sh 'scp your-app.jar user@production-server:/path'
            }
        }
    }
    post {
        always {
            script {
                // Always send an email after the job completes
                mail to: 'jayaarikaran@gmail.com',
                     subject: "Jenkins Build Notification: ${currentBuild.fullDisplayName}",
                     body: "The unit and integration tests have passed"
                     Jenkins Build: ${currentBuild.fullDisplayName}
                     Result: ${currentBuild.result}

                     Check the Jenkins logs for more details.

                     Build URL: ${env.BUILD_URL}
                     """,
                     attachLog: true
            }
        }
    }
}
