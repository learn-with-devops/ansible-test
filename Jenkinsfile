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
				try{
					checkout scm
					script{
						sh 'sh test.sh'
						sh 'ls -ltr > list.txt'
					}
				} catch(e){
					echo "catching the exception"
				} finally {
					echo "Final Block ececuted"
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
