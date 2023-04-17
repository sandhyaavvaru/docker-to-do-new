pipeline{
agent any {
   environment{
       DOCKERHUB_CREDENTIALS = credentials('dockerhub')
   }
    stage('continuous download') {
    git branch: 'main', url: 'https://github.com/sandhyaavvaru/docker-to-do-new.git'
}
    stage('continuous build') {
    sh 'docker build -t todo2 .'
}
    stage('login') {
    sh 'docker login -u $USERNAME -p $PASSWORD'
}
    stage('tag') {
    sh 'docker tag todo2 sandhyaavvaru/jenkins-todo:v2'
}
    stage('push') {
    sh 'docker push sandhyaavvaru/jenkins-todo:v2'
}
}
}
