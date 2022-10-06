pipeline {
  agent { 
  label 'ansible'
  }
  
  environment {
   AWS_EC2_PRIVATE_KEY=credentials('ec2-private-key') 
  }
  
  stages {
    
    //Get the Code from GitHub Repo
    stage('CheckOutCode'){
      steps{
        git branch: 'master',git credentialsId: '7dffcdbc-3ad3-4eb2-b277-52a4aa37bbd9', url: 'https://github.com/kiranmai2323/jenkins-with-ansible.git' 
      }
    }
     
    //Run the playbook
    stage('RunPlaybook') {
      steps {
        sh "ansible-playbook -i inventory/walmart.hosts --private-key=$AWS_EC2_PRIVATE_KEY playbooks/installTomcat.yml --ssh-common-args='-o StrictHostKeyChecking=no'"
      }
    }
  
  }//stages closing
}//pipeline closing
