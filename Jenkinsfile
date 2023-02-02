pipeline {
    environment {
        registry = 'kelseybreanna/flask_app'
        registryCredentials = 'docker'
        cluster_name = 'skillstorm'
    }
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Git') {
      steps {
        git(url: 'https://github.com/KelseyBurchard/flasking', branch: 'main')
      }
    }
stage('Build Stage') {
    steps {
        dockerImage = docker.build(registry)

        }
    }
}
stage('Deploy Stage') {
    steps {
        docker.withRegistry('', registryCredentials) {
            dockerImage.push()

            }
        }
    }
}