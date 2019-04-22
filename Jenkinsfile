#!groovy

@Library('keynes@master') _

pipeline {
  agent { label 'master' }
  options {
    buildDiscarder(logRotator(numToKeepStr:'15'))
    disableConcurrentBuilds()
    //skipDefaultCheckout()
    lock("seed")
    ansiColor('xterm')
  }
  stages {
    stage('init') {
      steps {
        script {
          properties(
            [
              [$class: 'GithubProjectProperty', displayName: '', projectUrlStr: 'https://github.com/AsociacionDrupalES/jenkins'],
              pipelineTriggers([githubPush()])
            ]
          )
        }
      }
    }
    stage('main') {
      steps {
        seed('admin/dev')
      }
    }
  }
}

