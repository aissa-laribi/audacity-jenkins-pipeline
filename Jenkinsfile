pipeline {
    agent any none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'ubuntu:latest'
                }
            }
            steps {
                sh '''#!/bin/bash
                    mkdir build && cd build
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