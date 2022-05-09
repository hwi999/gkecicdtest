pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/hwi999/gkecicdtest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
	gcloud builds submit --config cloudbuild.yaml
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
	sudo kubectl set image deployment webserver-blue webserver-container=gcr.io/jhj-01/imageview:blue_v2
        sudo kubectl set image deployment nginx ctn-nginx=gcr.io/jhj-01/imageview:green_v2
        '''
      }
    }
  }
}
