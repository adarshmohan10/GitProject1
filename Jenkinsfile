node {
stage ('scm') {
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/ganeshhp/helloworldweb.git']]])

}

stage ('build and package') {
sh 'mvn -f pom.xml clean package'

}

stage ('archive') {
archiveArtifacts 'target/*.war'
}

stage ('deploy and restart service') {
sh 'cp target/*war /opt/apache-tomcat-8.5.21/webapps/'
}
}
