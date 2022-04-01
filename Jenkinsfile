node('Dev') {
    stage('ContinuousDownload_Master') 
    {
     git 'https://github.com/ArkLearnersEdge/maven.git'
    }
    stage('ContinuousBuild_Master') 
    {
     sh 'mvn package'
   }
}
