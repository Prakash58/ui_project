node {
   
   stage('Code Checkout') { // ..for display purposes
     git credentialsId: 'GithubID', url: 'https://github.com/bharathanenenu/ui_project.git'
   }
   stage('Build') {
       withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.5.3') {
       sh 'mvn clean compile'
       }
   }
   stage('Test Execution') {
     withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.5.3') {
       sh 'mvn test'
       } 
   }
   stage('SonarQube Analysis') {
      //def job = build job: 'SonarJob'
      //withSonarQubeEnv("SonarQube") {
      //}
      withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.5.3') {
          sh ' mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar ' +
             ' -Dsonar.host.url=https://sonarcloud.io ' +
             ' -Dsonar.organization=cloudbhs '+ 
             ' -Dsonar.login=4b9b22956653ec6b5f6bf77418f4584b36dce13c ' +
             '-Dsonar.language=java ' +
             '-Dsonar.sources=. ' +
             '-Dsonar.tests=. ' +
             '-Dsonar.test.inclusions=**/*Test*/** ' +
             '-Dsonar.exclusions=**/*Test*/**'
          }
      }
   stage('Archive artifacts') {
     withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.5.3') {
       sh 'mvn install package'
       }
   }
   stage('Build Docker Image') {
    echo 'build docker image' 
   }
   
   stage('Deploy to Prod') {
     echo 'Deploy to Prod'
   }
}
