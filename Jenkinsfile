pipeline{
    
    agent { label "dev"};
    
    stages{
        stage("Code Cloning"){
            steps{
                git branch: 'master',
                url: "https://github.com/shreysiSwaraj/two-tier-flask-app.git", "master"
               }
            }
        }
        
        stage("Build"){
            steps{
                sh "docker build -t two-tier-flask-app ."
            }
            
        }
        stage("Testing"){
            steps{
                echo "Developer / Tester tests likh ke dega..."
            }
            
        }
        stage("Push to Docker Hub"){
            steps{
                script{
                    docker_push("dockerHubCreds","two-tier-flask-app")
                }  
            }
        }
        stage("Deploy"){
            steps{
                sh "docker compose up -d --build flask-app"
            }
        }
    }


}
