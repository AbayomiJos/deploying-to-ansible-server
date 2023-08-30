pipeline {
    agent any
    
    tools
    {
       maven "maven"
    }
    stages {
      stage('checkout') {
           steps {
                git branch: 'main', url: 'https://github.com/Yash-9/Congifxyz.git' 
          }
        }
      stage('Code Compile'){
	        steps{
			 sh "mvn compile"
			}
	   }
	  stage('JUNIT Test'){
	        steps{
			 sh "mvn test"
			}
	   }
	  stage('Packaging'){
	        steps{
			 sh "mvn package"
			}
	   } 
      stage('Tools Init') {
             steps {
               sh "ansible --version"
                    }
       }         
      stage('Ansible Deploy') {    
            steps {                          
                 sh "ansible-playbook webdeploy.yml -i localhost --user jenkins --key-file ~/.ssh/id_rsa"        
                  }
        }
    }
}
