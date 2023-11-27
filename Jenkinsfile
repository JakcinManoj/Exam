pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/JakcinManoj/Exam.git'
            }
        }

        
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_FxQD9x_Fec84SBAiHZuCeAkz8Rs | /usr/bin/docker login -u jakejake23 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker build -t jakejake23/exam .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker push jakejake23/exam'
            }
        }
        stage ('restart service') {
            steps {
                sh '/usr/bin/docker service update --image jakejake23/exam --force myservice'
            }
        }
    }
}

