//pipeline
pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat 'javac -d .src/*.java'
        bat 'echo Main-Class: Rectangulator > MANIFEST.MF'
        bat 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
      }
    }
    stage('run') {
      steps {
        bat 'java -jar rectangle.jar 7 9'
      }
    }
  }
  post {
    success {
      archiveArtifacts artifacts: 'rectangle.jar', fingerprint: true
    }
  }
}
