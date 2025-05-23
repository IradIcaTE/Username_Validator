pipeline {
    agent { label 'First' }

    parameters {
        string(name: 'USERNAME', defaultValue: 'Parth', description: 'Enter your username')
    }

    stages {
        stage('Validate Username') {
            steps {
                script {
                    def blockedUsers = ['admin', 'root', 'test']
                    def inputUser = params.USERNAME?.trim()

                    if (!inputUser) {
                        error("❌ Username cannot be empty!")
                    }

                    if (blockedUsers.contains(inputUser.toLowerCase())) {
                        error("🚫 Access denied: '${inputUser}' is a blocked username.")
                    }

                    echo "✅ Username '${inputUser}' is valid. Proceeding with the build..."
                }
            }
        }

        stage('Continue Work') {
            steps {
                echo "🎉 Welcome, ${params.USERNAME}! Build continues..."
            }
        }
    }
}
