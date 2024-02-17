pipeline
{
  agent any
  stages
  {
   stage ('git checkout')
    {
      steps
      {
        git 'https://github.com/thisisbbharat/EventWebsite.git'
      }
    }

     stage ('Nginx cleanup' )
    {
      steps
      {
        sh 'docker rm -f $(docker ps -aq) && docker rmi -f $(docker images -aq) '
             
      }
      
    }
    
    stage ('Nginx build' )
    {
      steps
      {
        sh 'docker build -t image:latest .'
      }
      
    }
    stage ('Nginx Deploy')
    {
      steps 
      {
        sh 'docker run -d -p 8081:80 image:latest'
      }
    }
  }
}
