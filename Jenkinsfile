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
	sudo gcloud builds submit --config cloudbuild.yaml
        '''
      }
    }
  }
}

