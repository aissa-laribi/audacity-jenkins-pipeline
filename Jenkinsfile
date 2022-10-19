pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'ubuntu:focal'
                    args '--user 0:0'
                }
            }
            steps {
                sh '''#!/bin/bash
                    apt-get update &&  apt-get install -y build-essential cmake git python3-pip
                    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends libgtk2.0-dev libasound2-dev libjack-jackd2-dev uuid-dev mosquitto
                    pip3 install conan --user
                    cd build
                    cmake -G "Unix Makefiles" ../
                    make -j`nproc`
                '''
            }
        }
    }
}