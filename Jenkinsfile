@Library('Shared') _
pipeline {
    agent any
    
    environment{
        SONAR_HOME = tool "Sonar"
    }
    
    parameters {
        string(name: 'FRONTEND_DOCKER_TAG', defaultValue: '', description: 'Setting docker image for latest push')
        string(name: 'BACKEND_DOCKER_TAG', defaultValue: '', description: 'Setting docker image for latest push')
    }
    
    stages {
        stage("Validate Parameters") {
            steps {
                script {
                    if (params.FRONTEND_DOCKER_TAG == '' || params.BACKEND_DOCKER_TAG == '') {
                        error("FRONTEND_DOCKER_TAG and BACKEND_DOCKER_TAG must be provided.")
                    }
                }
            }
        }
        stage("Workspace cleanup"){
            steps{
                script{
                    cleanWs()
                }
            }
        }
        
        stage('Git: Code Checkout') {
            steps {
                script{
                    code_checkout("https://github.com/saiyedin786/Hero-capstone-project.git","main")
                }
            }
        }
        
        stage("Trivy: Filesystem scan"){
            steps{
                script{
                    trivy_scan()
                }
            }
        }

        stage("OWASP: Dependency check"){
            steps{
                script{
                    owasp_dependency()
                }
            }
        }
        
        stage("SonarQube: Code Analysis"){
            steps{
                script{
                    sonarqube_analysis("Sonar", "Hero-Capstone-Project", "hero-capstone-project")
                }
            }
        }
        
        stage("SonarQube: Code Quality Gates"){
            steps{
                script{
                    sonarqube_code_quality()
                }
            }
        }
        
        
                
                
            }
        }
        
        stage("Docker: Build Images"){
            steps{
                script{
                        dir('admin'){
                            docker_build("shopnow-admin","${params.BACKEND_DOCKER_TAG}","saiyedin786")
                        }
                    
                        dir('backend'){
                            docker_build("shopnow-backend","${params.BACKEND_DOCKER_TAG}","saiyedin786")
                        }
                    
                        dir('frontend'){
                            docker_build("shopnow-frontend","${params.FRONTEND_DOCKER_TAG}","saiyedin786")
                        }
                }
            }
        }
        
        stage("Docker: Push to DockerHub"){
            steps{
                script{
                    docker_push("shopnow-admin","${params.BACKEND_DOCKER_TAG}","saiyedin786") 
                    docker_push("shopnow-backend","${params.FRONTEND_DOCKER_TAG}","saiyedin786")
                    docker_push("shopnow-frontend","${params.FRONTEND_DOCKER_TAG}","saiyedin786")
                }
            }
        }
    }
    post{
        success{
            archiveArtifacts artifacts: '*.xml', followSymlinks: false
            build job: "Wanderlust-CD", parameters: [
                string(name: 'FRONTEND_DOCKER_TAG', value: "${params.FRONTEND_DOCKER_TAG}"),
                string(name: 'BACKEND_DOCKER_TAG', value: "${params.BACKEND_DOCKER_TAG}")
            ]
        }
    }
}
