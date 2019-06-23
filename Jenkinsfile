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

                script {
                    def request = [:]
                    request << ["name" : PROJECT_NAME]
                    httpRequest( url: "$GITHUB_API_URL/user/repos", authentication: 'github_token', contentType: 'application/json', httpMode: 'POST', requestBody: request)
                }



            }

        }
        stage('Create Jenkins jobs') {
            steps {
                echo("creating jenkins jobs")
            }

        }
    }
}
