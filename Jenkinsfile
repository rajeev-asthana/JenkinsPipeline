pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Building the Java application'
          }
        }

        stage('Test') {
          steps {
            echo 'Testing the application'
            echo "Get the DriverPath ${ChromeDriverPath}"
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying the application in Tomcat'
        input(message: 'Do you want to deploy application', id: 'yes')
      }
    }

  }
  environment {
    ChromeDriverPath = '/home/rajeev/ChromeDriver/ChromeDriver.sh'
  }
}