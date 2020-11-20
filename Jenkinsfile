#! groovy

pipeline {
	agent any
	stages{
		stage("CleanUp the WorkSpace"){
			steps{
				deleteDir()
			}
		}
		stage("Checkout the code"){
			steps{
				script{
					try {
                            sh "sh test.sh"
                        } catch (Exception err) {
                            echo 'Shell Script failed'
                        } finally {
                            echo "checkout success"
                        }
				}
			}
		}
		stage("Running the playbook"){
			steps{
				ansiblePlaybook(
					inventory: '/etc/ansible/hosts',
					playbook: 'tree_install.yml',
					extraVars: [package: 'wget']
				)
			}
		}
	}
}
