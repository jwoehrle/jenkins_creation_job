pipeline {
    agent any
    environment {
        PROJECT_NAME = "myTestProject"
        GITHUB_API_URL = "https://api.github.com"
        GITHUB_CREDENTIALS = credentials('github_token')
        request = load('./src/main/groovy/github.groovy')
    }
    stages {
        stage('Create Github Repo') {
            steps {
                echo("creating github repo")
                
                httpRequest( url: "$GITHUB_API_URL/user/repos", authentication: 'github_token', contentType: 'application/json', httpMode: 'POST', requestBody: request.createRequest())

            }

        }
        stage('Create Jenkins jobs') {
            steps {
                echo("creating jenkins jobs")
            }

        }
    }
}
