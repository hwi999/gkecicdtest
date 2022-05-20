pipeline {
  agent any
  stages {
    stage('docker build and push') {
      steps {
        sh '''
	sudo gcloud builds submit --config cloudbuild.yaml
        '''
      }
    }
    stage('deploy') {
      steps {
        sh '''
        sudo kubectl set image deployment main ctn-main=gcr.io/jhj-02/mainimage:blue2
	sudo kubectl set image deployment main ctn-main=gcr.io/jhj-02
/blogimage:green2
        sudo kubectl describe deploy main | grep Image
        sudo kubectl describe deploy blog | grep Image
        '''
      }
    }

  }
}

