#!/usr/bin/env groovy
pipeline {
    agent {
        node any
    }

    stages {
        stage('Build Image') {
            when {
                branch 'master'  //only run these steps on the master branch
            }

            // Jenkins Stage to Build the Docker Image
              steps {
              
                sh 'docker build -t knx-devops:v1 .' 
                 sh 'docker tag knx-devops hd333/knx-devops:v1'
                  
               
          }

        }

        stage('Publish Image') {
            when {
                branch 'master'  //only run these steps on the master branch
            }
            
            // Jenkins Stage to Publish the Docker Image to Dockerhub or any Docker repository of your choice.
             steps {
                 withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
                   sh  'docker push hd333/knx-devops:v1'
                
        }
        }
    }
}
}