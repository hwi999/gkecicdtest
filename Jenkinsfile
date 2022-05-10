pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git branch: 'master',
            credentialsId: 'github_access_token',
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
    stage('deploy k8s') {
      steps {
        sh '''
	sudo kubectl set image deployment webserver-blue webserver-container=gcr.io/jhj-02/mainimage:blue
	sudo kubectl set image deployment nginx ctn-nginx=gcr.io/jhj-02/blogimage:green
        '''
      }
    }
  }
}
