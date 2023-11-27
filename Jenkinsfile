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
        stage ('remove and create service') {
            steps {
                sh'/usr/bin/docker container rm test --force'
                sh'/usr/bin/docker container run -itd -p 9876:80 --name test jakejake23/exam '
                sh '/usr/bin/docker service rm myservice'
                sh '/usr/bin/docker service create --name myservice -p 9876:80 jakejake23/exam'
                sh '/usr/bin/docker service scale myservice=5'
            }
        }
    }
}

