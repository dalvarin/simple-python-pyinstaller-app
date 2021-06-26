pipeline {
    agent none 
    stages {
        stage('Init'){
            agent jenkins02
            steps {
                sh 'who am i'
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