pipeline{
    agent any
    tools {nodejs "nodejs"}
    stages{
        stage('code checkout from GitHub'){
            steps{
                git 'https://github.com/Abhilash-1201/NodeJsBoilerplateCode.git'
            }
        }
        stage('Code Quality Check via SonarQube'){
            steps{
                script{
                    def scannerHome = tool 'sonarqube-scanner';
                    withSonarQubeEnv(credentialsId: 'sonarqube_access_token'){
                        sh "${tool("sonarqube-scanner")}/bin/sonar-scanner \
                        -Dsonar.projectKey=currentproject \
                        -Dsonar.sources=. \
                        -Dsonar.css.node=. \
                        -Dsonar.host.url=http://3.15.224.245:9000 \
                        -Dsonar.login=sqp_ebc0d111e7b66cfb4d228a3b20f099b4c07a6a7d"
                        
                    }
                }
            }
        }
        stage('Install Project Dependencies'){
            steps{
                nodejs(nodeJSInstallationName: 'nodejs'){
                    sh "npm install"
                }
            }
        }
    }
}
