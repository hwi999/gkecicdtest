pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git branch: 'master',
            credentialsId: 'gothub_access_token',
            url: 'https://github.com/hwi999/gkecicdtest.git'
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
