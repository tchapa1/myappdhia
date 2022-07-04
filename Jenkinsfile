pipeline
{
	agent any
	stages {
		stage('Pull') {
				steps{
					script{
						checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[ credentialsId: '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', url: 'https://github.com/tchapa1/myappdhia.git']]])
						}
					}
				}
		stage('Build') {
				steps{
					script{
						sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml "
						}
					}
				}
		stage('docker') {
				steps {
					script{ sh "ansible-galaxy collection install community.docker"
						sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml"
						}
					}

				}

		}
}
