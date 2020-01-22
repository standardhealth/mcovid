def dockerHubRepo = "icgcargo/argo-docs"
def githubRepo = "icgc-argo/argo-docs"
def commit = "UNKNOWN" 
pipeline {
    agent {
        kubernetes {
            label 'program-service-executor'
            yaml """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: docker
    image: docker:18-git
    tty: true
    volumeMounts:
    - mountPath: /var/run/docker.sock
      name: docker-sock
  volumes:
  - name: docker-sock
    hostPath:
      path: /var/run/docker.sock
      type: File
"""
        }
    }
    stages {
        stage('Prepare') {
            steps {
                script {
                    commit = sh(returnStdout: true, script: 'git describe --always').trim()
                }
                script {
                    version = sh(returnStdout: true, script: 'cat ./website/package.json | grep "\"version\":" | cut -d \':\' -f2 | sed -e \'s/"//\' -e \'s/",//\'').trim()
                }
            }
        }

        stage('Test') {
            steps {
                sh "echo No Docusaurus Tests"
            }
        }

        stage('Build') {
            when { branch 'master' }
            steps {
                container('docker') {
                    withCredentials([usernamePassword(credentialsId:'argoDockerHub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh 'docker login -u $USERNAME -p $PASSWORD'
                    }
                    // DNS error if --network is default
                    sh "docker build --network=host . -t ${dockerHubRepo}:${commit} -t ${dockerHubRepo}:${version}-${commit}"

                    sh "docker push ${dockerHubRepo}:${commit}"
                    sh "docker push ${dockerHubRepo}:${version}-${commit}"


                }
            }
        }

        stage('Deploy to argo-dev') {
            when { branch 'master' }
            steps {
                build(job: "/ARGO/provision/docs", parameters: [
                     [$class: 'StringParameterValue', name: 'AP_ARGO_ENV', value: 'dev' ],
                     [$class: 'StringParameterValue', name: 'AP_ARGS_LINE', value: "--set-string image.tag=${commit}" ]
                ])
            }
        }

        stage('Deploy to argo-qa') {
            when { branch 'master' }
            steps {
                build(job: "/ARGO/provision/docs", parameters: [
                     [$class: 'StringParameterValue', name: 'AP_ARGO_ENV', value: 'qa' ],
                     [$class: 'StringParameterValue', name: 'AP_ARGS_LINE', value: "--set-string image.tag=${commit}" ]
                ])
            }
        }
    }
}