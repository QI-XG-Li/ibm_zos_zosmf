pipeline {
    agent none
    
    stages {
        stage('Build') {
            agent {
               node {
                   label 'zmf-ansible-configuration'
                   customWorkspace "workspace/${env.BRANCH_NAME}"
                    }
	    }
            steps {
                echo 'Hello, build'
		sh '/usr/local/bin/ansible --version' 
                sh 'git clone git@github.com:IBM/ibm_zos_zosmf.git' 
                sh '/usr/local/bin/ansible-galaxy collection build'
	        sh '/usr/local/bin/ansible-galaxy collection install ibm-ibm_zos_zosmf-2.0.1.tar.gz'
            }
        }

        stage('Test') {
            agent {
               node {
                   label 'zmf-ansible-configuration'
                   customWorkspace "workspace/${env.BRANCH_NAME}"
                    }
	    }
            steps {
                echo 'Hello, Test12'
		sh 'pwd'
		sh 'sed -i '' 's/zosmf1.ibm.com/pev211.pok.ibm.com/g' /Users/strangepear2019/ansible_20200609/workspace/feature/0/CICD/playbooks/hosts'
                sh '/usr/local/bin/ansible-playbook ~/.ansible/collections/ansible_collections/ibm/ibm_zos_zosmf/playbooks/sample_role_job_complete.yml'
            }
        }
    }
}