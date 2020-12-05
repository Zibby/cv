pipeline {
  agent any
  stages {
    stage('Build') {
      agent {
        docker {
          image 'zibby/latex'
        }

      }
      steps {
        script {
          sh 'xelatex cv'
          sh 'xelatex cv'
        }

        stash 'cv.pdf'
      }
    }

    stage('Deploy') {
      steps {
        unstash 'cv.pdf'
        sh 'cp cv.pdf /opt/cv/'
      }
    }

  }
}
