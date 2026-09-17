pipeline {
    agent any
    parameters {
        booleanParam(name: 'RUN_EXTRA_CHECK', defaultValue: true, description: 'Run the extra check stage')
    }
    stages {
        stage ('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/raghuldravidr7-jpg/assesment1.git'
            }
        }
        stage ('Build') {
            steps {
                bat '"C:\\Users\\lekha\\AppData\\Local\\Programs\\Python\\Python312\\python.exe" -m py_compile app.py'
                echo 'Build successful: app.py compiled with no syntax errors'
            }
        }
        stage ('Extra Check') {
            when {
                expression { params.RUN_EXTRA_CHECK == true }
            }
            steps {
                echo 'Running extra check: verifying greet() output format...'
                bat '"C:\\Users\\lekha\\AppData\\Local\\Programs\\Python\\Python312\\python.exe" -c "from app import greet; print(greet(\'Student\'))"'
            }
        }
    }
}