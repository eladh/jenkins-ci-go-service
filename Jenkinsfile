#!/usr/bin/env groovy
import groovy.json.JsonSlurper

node {

    def server_url = "http://jfrog.local/artifactory"


    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */
        git url: 'https://github.com/eladh/jenkins-ci-go-service.git', branch: 'master'
    }

    stage('Prep') {


        /* Configure jfrog cli
         withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: CREDENTIALS, usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) {
              sh "jfrog rt c beta --user ${USERNAME} --password ${PASSWORD} --url ${server_url} < /dev/null"
         }

    }

   stage('Build Modules') {
             steps {
                     script {
                         sh "make build"
                     }
             }
   }


    stage('Publish') {
              environment {
                  DEMO_VERSION = 1
              }
              steps {
                      script {
                          echo "Publishing all modules with version: ${env.DEMO_VERSION}"
                          sh "make publish"
                     }
              }
     }
}
