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
                    apt-get update && apt-get install -y build-essential cmake git python3-pip 
                    apt-get install -y libgtk2.0-dev libasound2-dev libjack-jackd2-dev uuid-dev mosquitto
                    pip3 install conan --user
                    cd build
                    cmake -G "Unix Makefiles" ../
                    make -j`nproc`
                '''
            }
        }
    }
}