pipeline {
        agent none
          options {
            disableConcurrentBuilds()
            skipDefaultCheckout()
            timestamps()
        }
        stages {
            stage('Build') {
                parallel {
                    stage('amd64') {
                        agent {
                            docker {
                                image "vyos/vyos-build:current"
                                alwaysPull true
                            }
                        }
                        steps {
                          echo "Hello from amd64"
                          sh """
                            pwd
                            ls -al
                            echo "Hello from inside the container amd64"
                          """
                        }
                    }
                    stage('arm64') {
                        agent {
                            docker {
                                image "vyos/vyos-build:current-arm64"
                                alwaysPull true
                            }
                        }
                        steps {
                          echo "Hello from arm64"
                          sh """
                            pwd
                            ls -al
                            echo "Hello from inside the container arm64"
                          """
                        }
                    }
                }
            }
        }
}
