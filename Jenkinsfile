pipeline {
    agent any
    environment {
        JOB_HOME_DIR = '/home/jeevan/Desktop/JenkinsJob'
    }
    stages {
        stage('Setup') {
            steps {
                sh label: 'Changing directory to the build',  script: 'cd ${JOB_HOME_DIR}'
                git branch: 'main', credentialsId: 'jeevan_git_hub_cred', poll: false, url: 'https://github.com/Jeevanandan819/jenkins-python-test.git'
                sh label: 'changing directory to test_repo', script: 'cd jenkins-python-test'
                sh label: 'creating the virtual environment', script: 'python3 -m venv .venv'
                sh label: 'Activating the venv', script: 'source .venv/bin/activate'
                sh label: 'Installing the python packages', script: 'pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                sh label: 'Invoking pytest', script: 'pytest'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}