 stage('Update Deployment File') {
        environment {
            GIT_REPO_NAME = "Java-springboot-appmanifest"
            GIT_USER_NAME = "Teja-Chittamuri"
        }
        steps {
            withCredentials([string(credentialsId:'github', variable: 'GITHUB_TOKEN')]) {
                sh '''
                    git config user.email "tejschittamuri@gmail.com"
                    git config user.name "Teja Chittamuri"
                    BUILD_NUMBER=${BUILD_NUMBER}
                    cat deployment.yaml
                    sed -i 's+tejachittamuri/springbootappcicd.*+tejachittamuri/springbootappcicd:${DOCKERTAG}+g' deployment.yaml
                    cat deployment.yaml
                    git add deployment.yaml
                    git commit -m "Update deployment image to version ${env.BUILD_NUMBER}"
                    git push https://${GITHUB_TOKEN}@github.com/${GIT_USER_NAME}/${GIT_REPO_NAME} HEAD:master
                '''
            }
        }
    }
