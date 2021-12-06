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
   }
}

