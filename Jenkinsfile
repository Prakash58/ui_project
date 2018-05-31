node {
   
   stage('Code Checkout') { // ...for display purposes
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
   stage('Archive artifacts') {
     withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.5.3') {
       sh 'mvn install package'
       }
   }
   stage('Build Docker Image') {
    echo 'build docker image' 
   }
   
   stage('Deploy to Dev') {
     echo 'Deploy to Dev'
   }
}
