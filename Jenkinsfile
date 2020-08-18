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

        stage('Test log') {
          steps {
            writeFile(file: 'LogTestFile.txt', text: 'This is an automation file log')
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        input(message: 'Do you want to deploy application', id: 'yes')
        echo 'Deploying the application in Tomcat'
      }
    }

  }
  environment {
    ChromeDriverPath = '/home/rajeev/ChromeDriver/ChromeDriver.sh'
  }
}