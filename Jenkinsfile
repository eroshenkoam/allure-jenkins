pipeline {
    agent any

    parameters {
        booleanParam(name: 'PERFORM_BUILD', defaultValue: false, description: 'Perform build?')
    }

    stages {
        stage('Build') {
            when { expression { return params.PERFORM_BUILD } }
            steps {
                withAllureUpload(projectId: '1', results: [[path: 'build/allure-results']]) {
                    sh './gradlew clean test'
                }
            }
        }
    }
}
