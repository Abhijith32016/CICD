pipeline {
    agent any

    environment {
        VENV = "venv"
    }

    stages {
        stage('Clone GitHub Repo') {
            steps {
                git branch: 'main', credentialsId: 'github-https', url: 'https://github.com/Abhijith32016/CICD'
            }
        }

        stage('Set Up Python Virtual Environment') {
            steps {
                // Use the 'python' command from the system's PATH to create the virtual environment.
                bat 'python -m venv venv'
                
                // Now, use the Python executable located inside the newly created virtual environment
                // to install and upgrade packages.
                bat '.\\venv\\Scripts\\python.exe -m pip install --upgrade pip'
                bat '.\\venv\\Scripts\\pip install -r requirements.txt'
            }
        }

        stage('Run Flask App') {
            steps {
                // Finally, run the Flask application using the Python executable from the venv.
                bat '.\\venv\\Scripts\\python.exe app.py'
            }
        }
    }
}
