https://github.com/arnaud-deprez/demo-jenkins-pipeline-gradle

Jenkinsfile

try {
  timeout(time: 1, unit: 'MINUTES') {
    //def appName="${APP_NAME}"
    def project=""
    node {
      stage("build") {
        project = env.PROJECT_NAME
        //sh "gradle -version"
        sh "mvn -version"
      }
    }
  }    
} catch (err) {
             echo "in catch block"
             echo "Caught: ${err}"
             currentBuild.result = 'FAILURE'
             throw err
  }
