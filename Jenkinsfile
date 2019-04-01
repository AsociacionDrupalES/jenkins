#!groovy

@Library('keynes@master') _

pipeline {
  agent { label 'master' }
  options {
    buildDiscarder(logRotator(numToKeepStr:'15'))
    disableConcurrentBuilds()
    gitLabConnection('gitlab')
    //skipDefaultCheckout()
    lock("seed")
    ansiColor('xterm')
  }
  triggers {
    gitlab(
      triggerOnPush: true,
      branchFilterType: 'NameBasedFilter',
      includeBranchesSpec: 'master',
      excludeBranchesSpec: '',
     )
  }
  stages {
    stage('main') {
      steps {
        seed()
      }
    }
  }
}

