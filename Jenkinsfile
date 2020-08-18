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
          environment{
            LocalVariable = "HelloLocal"
          }

          steps {
            writeFile(file: 'LogTestFile.txt', text: "This is the chrome driver path ${ChromeDriverPath} and localvariable value ${LocalVariable}")
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            input(message: 'Do you want to deploy application', id: 'yes')
            echo 'Deploying the application in Tomcat'
          }
        }

        stage('Artifact') {
          steps {
            archiveArtifacts 'LogTestFile.txt'
          }
        }

      }
    }

  }
  environment {
    ChromeDriverPath = '/home/rajeev/ChromeDriver/ChromeDriver.sh'
  }
}