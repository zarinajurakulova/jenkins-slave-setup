pipeline {
    agent {
	docker {
		image 'ansible/ansible:default'
	}
    }
    stages {
        stage("Lint role using molecule") {
            steps {
                sh """
                    molecule lint
                """
            } //steps
        } //stage
        stage("Deploy role in test Docker containers") {
            steps {
                sh """
                   molecule converge
                """
            } //steps
        } //stage
        stage("Destroy test Docker container") {
            steps {
                sh """
                    molecule destroy
                """
            } //steps
        } //stage
    } //stages
} //pipeline
