pipeline
{
agent any
stages
{
 stage('scm checkout: download code from github')
 {steps { git branch: 'master', url: 'https://github.com/yashighokar1412/mavenproject.git'  }}


 stage('execute unit test framework')
 {steps { withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn test'
} } }


 stage('generate artifact')
 {steps { withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
    sh 'mvn package'
} } }
  
 
 stage('sonar analysis')
 {steps { withSonarQubeEnv(credentialsId: 'sonar', installationName: 'sonar') 
     {sh 'sonar:sonar'} 
} } }

}
