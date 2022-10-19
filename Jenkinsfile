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
                    apt-get update && apt-get install -yq tzdata
                    ln -fs /usr/share/zoneinfo/America/New_York /etc/localtime
                    dpkg-reconfigure -f noninteractive tzdata
                    apt-get update &&  apt-get install -y build-essential cmake git python3-pip
                    apt-get install -y libgtk2.0-dev libasound2-dev libjack-jackd2-dev uuid-dev mosquitto
                    pip3 install conan --user
                    mkdir build && cd build
                    cmake -G "Unix Makefiles" ../audacity-pipeline
                    make -j`nproc`
                '''
            }
        }
    }
}