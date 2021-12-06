pipeline{
    agent any
  stages{
         stage('Git clone') {
            steps {
             git branch: 'main', changelog: false, poll: false, url: 'https://github.com/jishoy-cloudjournee/python-djanjo-login.git'
              sh 'ls'
            }
         }
       stage('Build Docker') { 
              steps
              {
                sh 'docker build -t jishoy96/django .'
              }
          }
  
      stage('Deploy'){
        steps { 
             script {
              docker.withRegistry(
                'https://519852036875.dkr.ecr.us-west-1.amazonaws.com',
                'ecr:us-west-1:my.awsecr.id') {
                 def myImage = docker.build('jishoy-ecr')
                 myImage.push('latest')
                }
           }
       }
     }
  }
}

