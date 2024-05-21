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


stage('sonar analysis & generate artifacts')
 {steps {  withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) 
    { withSonarQubeEnv(credentialsId: 'sonar', installationName: 'sonar') 
     { sh 'mvn package sonar:sonar'} 
} } }

}
