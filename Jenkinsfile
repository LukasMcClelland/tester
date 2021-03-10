def project = 'lukas.test'
 
 
pipeline {
    agent {
        label 'linux'
    }
    options {
        timeout(time: 2, unit: 'HOURS')
    }
    stages { 
        stage("Setup dev environment") {
            steps {
                sh """
                    export PIP_DOWNLOAD_CACHE=/scratch/pip_download_cache
                    rm -rf /scratch/unicon-dev
                    cd /scratch
                    /usr/bin/python3.6 -m venv unicon-dev
                    . /scratch/unicon-dev/bin/activate
                    pip install --upgrade pip
                    pip3 install wheel asyncssh cryptography==3.3.1 pytest pytest-xdist
                """
            }
        } 
    }
    post {
        cleanup {
            cleanWs()
        }
    }
}
