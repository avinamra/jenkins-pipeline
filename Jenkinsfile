pipeline {
    agent any


    stages 
    {  
        
        stage ('SCM Checkout') {
          git 'https://https://github.com/avinamra/jenkins-pipeline'
         }
    
    }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven') 
                {   
                    sh 'mvn compile' 
                }
                }
                  }
                                
            
        
        
        stage ('Testing Stage') {


            steps {
                withMaven(maven : 'maven')
                {
                    sh 'mvn test'
                }
                  }
                                 
        }

        
        stage ('install Stage') {
            steps {
                withMaven(maven : 'maven')
                {
                    sh 'mvn install'
                }
                                  
                   }
        }

        stage ('deploy to tomcat') {
          steps {
              sshagent(['ssh-key']) {
                 sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.43.64:/var/lib/tomcat/webapps'
    }      
}
        }
    }
}
