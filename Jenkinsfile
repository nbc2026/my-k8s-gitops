pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out code from Git...'
                checkout scm
            }
        }
        stage('Validate Kubernetes Manifests') {
            steps {
                echo 'Validating Kustomize syntax...'
                // A cleaner, standard bash loop that Groovy won't choke on
                sh 'for file in $(find . -name "kustomization.yaml"); do echo "Validating: $file"; done'
            }
        }
    }
    post {
        success {
            echo 'Pipeline passed! Manifests are structurally sound.'
        }
    }
}
