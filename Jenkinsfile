pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/ivanholoburda/lab-4-ci-cd.git'            }
        }
        
        stage('Build') {
            steps {
                // Крок для збірки проекту з Visual Studio
                // Встановіть правильні шляхи до рішення/проекту та параметри MSBuild
		bat '"C:\\Program Files\\Microsoft Visual Studio\\2022\\Community\\MSBuild\\Current\\Bin\\MSBuild.exe" test_repos.sln /t:Build /p:Configuration=Release'
            }
        }

        stage('Test') {
            steps {
                bat "x64\\Debug\\test_repos.exe --gtest_output=xml:test_report.xml"
            }
        }
    }

    post {
    always {
	junit "test_report.xml"
    }
}
}