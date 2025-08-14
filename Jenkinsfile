pipeline {
    agent any

    environment {
        VENV = "venv"
        // TODO: Replace this placeholder with the actual, correct path to your python.exe
        // You can find this by running 'where python' in your command prompt.
        PYTHON_EXE = 'C:\\Users\\ramay\\AppData\\Local\\Programs\\Python\\Python313\\python.exe'
    }

    stages {
        stage('Clone GitHub Repo') {
            steps {
                // Ensure this URL is correct and the credential has access to it.
                git branch: 'main', credentialsId: 'github-https', url: 'https://github.com/Abhijith32016/CICD'
            }
        }

        stage('Set Up Python Virtual Environment') {
            steps {
                echo 'Setting up Python virtual environment...'
                // Use the hardcoded path from the environment block to run python.exe
                bat "${env.PYTHON_EXE} -m venv ${env.VENV}"
                
                // Now, use the Python executable located inside the newly created virtual environment
                // to install and upgrade packages.
                bat ".\\${env.VENV}\\Scripts\\python.exe -m pip install --upgrade pip"
                bat ".\\${env.VENV}\\Scripts\\pip install -r requirements.txt"
            }
        }

        stage('Run Flask App') {
            steps {
                // Finally, run the Flask application using the Python executable from the venv.
                bat ".\\${env.VENV}\\Scripts\\python.exe app.py"
            }
        }
    }
}
