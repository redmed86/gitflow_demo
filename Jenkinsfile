#!/usr/bin/env groovy
node{
  def branch = "${env.BRANCH_NAME}"

  stage ('Checkout') {
    //checkout the ctsupport.bot project
    checkout scm
    echo "You are building the following branch: " + branch
  }

  stage ('Build') {
    echo 'This is where your build code goes.  You can build maven, nodejs, docker, go, or anyother project that you can build with a cli.'
  }

  if(env.BRANCH_NAME.startsWith('feature/')) {
      stage('Deploy to Dynamic Dev Instance and run Test Automation'){
        echo "Execute Test Automation Suite"
      }
  }

  if(env.BRANCH_NAME.startsWith('PR-')){
    stage('Merge Validation'){
      echo "run merge validation script with auto approval for PR on success!"
    }
  }

  if (env.BRANCH_NAME.equalsIgnoreCase('master')){
  //run all functionality that should run in develop
    stage ('Deploy to Staging') {
        echo "This is where your deploy code would go. You can run a script or interact with a plugin for this step!"
    }

    stage('Custom Test Script Execution'){
      echo 'This is where you run a custom test script to verify your staging environment works'
    }

    stage('Switch Routes') {
      echo 'This is where you would run that command that would switch your production routes from current Production to staging version.'
    }
  }
}
