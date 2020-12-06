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
          DATE = sh("date '+%d-%m-%Y'") 
          sh "sed -i \"s/__DATE__/${DATE}/g\" cv.tex"
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
