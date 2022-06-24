pipeline { 

    environment { 

        registry = "devopshub123/flaskdemo" 

        registryCredential = 'devopshub123' 

        dockerImage = 'flask_test' 

    }

    agent any 

    stages { 

        stage('Cloning our Git') { 

            steps { 

                git 'https://github.com/bhargavsiripurapu/flask_demo.git' 

            }

        } 

        stage('Building our image') { 

            steps { 

                script { 

                    dockerImage = docker.build registry + ":latest" 

                }

            } 

        }

        stage('Deploy our image') { 

            steps { 

                script { 

                    docker.withRegistry( '', registryCredential ) { 

                        dockerImage.push() 

                    }

                } 

            }

        } 

        stage('Cleaning up') { 

            steps { 

                sh "docker rmi flask_test:latest" 

            }

        } 

    }

}