pipeline{
    agent any
    environment {
        registry = '519852036875.dkr.ecr.us-west-1.amazonaws.com/jishoy-ecr'
        registryCredential = 'my.awsecr.id'
        dockerImage = ''
    }
    
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
                //sh 'docker build -t jishoy96/django .'
                script {
                  dockerImage = docker.build registry + ":$BUILD_NUMBER"
                 }
              }
          }
  
       stage('Deploy image') {
        steps{
            script{
                docker.withRegistry("https://" + registry, "ecr:eu-central-1:" + registryCredential) {
                    dockerImage.push()
                }
            }
        }
     }
  }
}

