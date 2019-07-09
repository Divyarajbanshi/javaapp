node {

stage('GIT Clone'){
git credentialsId: 'GitHubPwd', url: 'https://github.com/Divyarajbanshi/javaapp.git'
}

stage('Maven Build'){
def mvnHome = tool name: 'maven-3', type: 'maven'
sh "${mvnHome}/bin/mvn package"
}

stage('Deploy to tomcat'){
sshagent(['rootuser']) {
sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/maven-pipeline-build/target/JenkinsWar.war /opt/tomcat/apache-tomcat-8.5.42/webapps/'
}

}




}
