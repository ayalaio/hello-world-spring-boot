pipeline {

    agent any

    tools {
        docker 'docker-latest' 
    }

    stages {
        stage('Build') {
            steps {
              script {
                def dockerTool = tool name: 'docker-latest', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
                dockerTool.withTool("docker-default") { 

                  withDockerServer([credentialsId: "jenkins", uri: "http://nexus.capitola.cafe/repository/docker-dev/"]) { 

                    sh "printenv" 
                    sh "docker images" 
                    // base = docker.build("flyvictor/victor-wp-build") 
                    // base.push("tmp-fromjenkins") 
                  } 
                }
              }
              
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
