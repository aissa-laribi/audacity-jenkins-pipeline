pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'ubuntu:latest'
                    args '--user 0:0'
                }
            }
            steps {
                sh '''#!/bin/bash
                    apt-get update && apt-get install -y cmake
                    ls
                    cd build
                    pwd
                    cmake -G "Unix Makefiles" ../audacity
                    make -j`nproc`
                    cd bin/Debug
                    mkdir "Portable Settings"
                    ./audacity
                    cd ../../..
                    pwd
                    make install

                '''
            }
        }
    }
}