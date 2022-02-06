pipeline {
      agent any
    stages{
        stage('Build artifact'){
            steps{
               sh label: 'compile-hello-world', script: 'mvn -B -f pom.xml clean install'
            }
        }
          
        stage('Build Image'){
            steps{
               sh 'sudo docker build -t Ail9010o:${BUILD_NUMBER} .'
            }
        }
           
        stage('Publish Image'){
            steps{
               withCredentials([string(credentialsId: 'dockerhubPwd', variable: 'dockerhubPwd')]) {
                  sh 'sudo docker login --username Ail9010ord ${dockerhubPwd}'
                }
               sh 'sudo docker push Akil9010BUILD_NUMBER}'
            }
            post{
               success{
                  sh 'sudo docker rmi -f Akil9010BUILD_NUMBER}'
               }
            }
        }

       

        

    }
}
