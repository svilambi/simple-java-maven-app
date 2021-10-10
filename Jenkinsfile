node{

  git branch: "master", url: "https://github.com/svilambi/simple-java-maven-app.git" 

  stage('Unit Tests') {
    withEnv(["JAVA_HOME=${ tool "java-11" }", "PATH+MAVEN=${ tool "maven3.8.3" }/bin:${env.JAVA_HOME}/bin"]) {
        sh "mvn test"
    }
  }

  stage ('Sonarqube') {
    withEnv(["JAVA_HOME=${ tool "java-11" }", "PATH+MAVEN=${ tool "maven3.8.3" }/bin:${env.JAVA_HOME}/bin"]) {
        sh "mvn sonar:sonar -Dsonar.host.url=http://192.168.1.9:9000"
    }
  }

  stage ('Build Jar') {
    withEnv(["JAVA_HOME=${ tool "java-11" }", "PATH+MAVEN=${ tool "maven3.8.3" }/bin:${env.JAVA_HOME}/bin"]) {
        sh "mvn clean package -Dmaven.test.skip=true"
    }
  }
  
}
