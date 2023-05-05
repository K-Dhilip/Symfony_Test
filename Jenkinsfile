pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'composer install'
      }
    }

    stage('test') {
      parallel {
        stage('Unitaire') {
          steps {
            bat 'php bin/phpunit tests/unit'
          }
        }

        stage('integration ') {
          steps {
            bat 'php bin/phpunit tests/integration'
          }
        }

        stage('Fonctionnel ') {
          steps {
            bat 'php bin/phpunit tests/functional'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        bat 'symfony server:start'
      }
    }

  }
}