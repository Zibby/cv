pipeline {
  agent any
  stages {
    stage('Git Clone') {
      steps {
        git 'https://github.com/zibby/cv'
      }
    }

    stage('Build') {
      agent {
        docker {
          image 'zibby/latex'
        }

      }
      steps {
        script {
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