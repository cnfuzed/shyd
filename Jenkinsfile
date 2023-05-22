pipeline {
  agent any

  stages {
    stage('Terraform Apply') {
      steps {
        sh 'terraform init -no-color'
        sh 'terraform apply -auto-approve -no-color'
      }
    }

    stage('Ansible Provisioning') {
      steps {
	dir('/var/lib/jenkins/workspace/shyd/'){
	ansiblePlaybook(
                    playbook: 'path/to/your/playbook.yml',
                    inventory: 'path/to/your/inventory.ini',
                    extraVars: [
                        ansible_ssh_common_args: '-vvv'
                    ]
                )
        sh 'ansible-playbook -i inventory.ini ansible/playbook.yml'
      }
    }
 }
  }
}

