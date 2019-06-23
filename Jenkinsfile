import groovy.json.JsonOutput

pipeline {
    agent any
    environment {
        PROJECT_NAME = "myTestProject"
        GITHUB_API_URL = "https://api.github.com"
        GITHUB_CREDENTIALS = credentials('github_token')
    }
    stages {
        stage('Create Github Repo') {
            steps {
                echo("creating github repo")

                script {
                    def request = [
                            name: "$PROJECT_NAME"
                    ]
                    def json = JsonOutput.toJson(request)
                    httpRequest( url: "$GITHUB_API_URL/user/repos", authentication: 'github_token', contentType: 'APPLICATION_JSON', httpMode: 'POST', requestBody: json)
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
