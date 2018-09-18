pipeline {
    agent any 
      stages {
          stage ('Checkout Git repository') {
              steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/nishanka84/helloworld.git']]])
            }
          }
          stage ('package stage') {
              steps {
                  withMaven(maven : 'maventest') {
                 sh 'mvn clean package'
                  }
              }
          }
         stage ('Test stage') {
              steps {
                  withMaven(maven : 'maventest') {
                 sh 'mvn test'
                  }
              }
          }
         stage ('Deploy stage') {
              steps {
                build 'tomcat deploy'
              }
          }
      }
}
