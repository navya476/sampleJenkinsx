pipeline {
  environment{
    VERTICAL = 'sample'
  }
  agent {
    kubernetes {
      label 'sample'
      yaml """
apiVersion: v1
kind: Pod
metadata:
spec:
  containers:
  - name: docker
    image: docker:dind
    tty: true
    securityContext:
      privileged: true
"""
    }
  }
  stages {
    stage('build') {
      steps {
        container('docker') {
          sh '''
            echo "This is build"
	    sleep 3
	    docker version
          '''
        }
      }
    }
    stage('tag & push') {
      steps {
        container('docker') {
          sh '''
            echo "This is to tag and push"
	    sleep 3
          '''
        }
      }
    }
  }
}
