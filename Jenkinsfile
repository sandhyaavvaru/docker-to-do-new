pipeline{
   agent { 
      label 'docker'
   }
   environment{
       DOCKERHUB_CREDENTIALS = credentials('dockerhub')
   }
   stages{
    stage('continuous download') {
       steps{
          git branch: 'main', url: 'https://github.com/sandhyaavvaru/docker-to-do-new.git'
       }
    }
    stage('continuous build') {
       steps{
          sh 'docker build -t todo2 .'
       }
    }
    stage('login') {
       steps{
          sh 'docker login -u $USERNAME -p $PASSWORD'
       }
    }
    stage('tag') {
       steps{
          sh 'docker tag todo2 sandhyaavvaru/jenkins-todo:v2'
       }
    }
    stage('push') {
       steps{
          sh 'docker push sandhyaavvaru/jenkins-todo:v2'
       }
    }
   }
}
