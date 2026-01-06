pipeline {
    agent any
    stages {
        stage('Pobranie kodu') {
            steps {
                // Jenkins sam robi "git clone" automatycznie,
                // więc tu tylko sprawdzamy, czy pliki są na miejscu.
                sh 'ls -la'
            }
        }
        
        stage('Wdrożenie na K3s') {
            steps {
                echo 'Wdrażam konfigurację z repozytorium...'
                // Teraz używamy pliku, który Jenkins pobrał z GitHuba!
                sh 'kubectl apply -f deployment.yaml --insecure-skip-tls-verify'
            }
        }
        
        stage('Status') {
            steps {
                sh 'kubectl get pods --insecure-skip-tls-verify'
            }
        }
    }
}