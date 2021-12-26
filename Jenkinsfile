pipeline {
    agent {
        label 'ansible'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: '1011', credentialsId: 'Yandex', url: 'git@github.com:anguisa/mnt-homeworks-ansible.git'
            }
        }
        stage('Install requirements') {
            steps {
                sh 'pip3 install -r test-requirements.txt'
            }
        }
        stage('Run molecule') {
            steps {
                sh 'mkdir -p molecule/default/roles/elasticsearch-role'
                sh 'ln -sf `pwd` molecule/default/roles/elasticsearch-role'
                sh 'molecule test'
            }
        }
    }
}
