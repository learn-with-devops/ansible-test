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
				checkout scm
				scripts{
					echo "Running scripts line"
				}
			}
		}
		stage("Running the playbook"){
			steps{
				ansiblePlaybook(
					inventory: '/etc/ansible/hosts',
					playbook: 'tree_install.yml'
				)
			}
		}
	}
}
