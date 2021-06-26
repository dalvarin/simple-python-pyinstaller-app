pipeline {
    agent none 
    stages {
        stage('Init'){
            agent { label 'linux' }
            steps {
                sh 'who am i'
                sh 'id'
                sh 'pwd'
            }
        }
        stage('Build') { 
            agent {
                docker {
                    image 'python:2-alpine' 
                }
            }
            steps {
                sh 'python -m py_compile sources/add2vals.py sources/calc.py' 
                stash(name: 'compiled-results', includes: 'sources/*.py*') 
            }
        }
    }
}