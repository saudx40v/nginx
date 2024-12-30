pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                echo "Cloning repository from GitHub"
                git url: 'https://github.com/username/repository.git', branch: 'main' // استبدلها برابط مستودعك
            }
        }
        stage('Install Dependencies') {
            steps {
                echo "Installing dependencies"
                script {
                    // إذا كان لديك ملف requirements.txt (Python)
                    if (fileExists('requirements.txt')) {
                        sh 'pip install -r requirements.txt'
                    }
                    // أو إذا كان لديك package.json (Node.js)
                    else if (fileExists('package.json')) {
                        sh 'npm install'
                    }
                    // إذا كان لديك ملف pom.xml (Java)
                    else if (fileExists('pom.xml')) {
                        sh 'mvn install'
                    }
                }
            }
        }
        stage('Run Tests') {
            steps {
                echo "Running tests to ensure code works correctly"
                script {
                    // إذا كان لديك اختبارات في Python
                    if (fileExists('requirements.txt')) {
                        sh 'pytest' // أو أي أمر آخر لتشغيل اختبارات Python
                    }
                    // إذا كان لديك اختبارات في Node.js
                    else if (fileExists('package.json')) {
                        sh 'npm test' // أو أي أمر آخر لتشغيل اختبارات Node.js
                    }
                    // إذا كان لديك اختبارات Java (Maven)
                    else if (fileExists('pom.xml')) {
                        sh 'mvn test' // أو أي أمر آخر لتشغيل اختبارات Java
                    }
                    // إذا لم يكن هناك اختبارات معرفة
                    else {
                        echo 'No tests found in the repository'
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution complete.'
        }
        success {
            echo 'Tests passed successfully!'
        }
        failure {
            echo 'Some tests failed. Please check the logs.'
        }
    }
}
