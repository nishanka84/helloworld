pipeline {
    agent any 
        tools {
        maven 'maventest' 
    }
      stages {
          stage ('Checkout Git repository') {
              steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/nishanka84/helloworld.git']]])
            }
          }
          stage ('package stage') {
              steps {
                 sh 'mvn clean package'
              }
          }
         stage ('Test stage') {
              steps {
                 sh 'mvn test'
              }
          }
         stage ('Deploy stage') {
              steps {
                build 'tomcat deploy'
              }
          }
      }
}
