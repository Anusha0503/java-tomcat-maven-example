node {

  stage ('checkout'){
           git branch: 'master', credentialsId: 'gitcredentials', url: 'https://github.com/Anusha0503/java-tomcat-maven-example.git'
 
         }

   stage ('build'){ 
        withMaven(globalMavenSettingsConfig: '', jdk: 'java', maven: 'maven', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn clean deploy'
           }
   
   }
   stage ('sonarscan'){
     withMaven(globalMavenSettingsConfig: '', jdk: 'java', maven: 'maven', mavenSettingsConfig: '', traceability: true) {
    sh  "mvn sonar:sonar \
  -Dsonar.projectKey=java-tomcat-maven-example \
  -Dsonar.host.url=http://3.88.168.185:9000 \
  -Dsonar.login=30c1163fcda0fede4ac143ed3118670f8fcf8036"
   }
   }
}
