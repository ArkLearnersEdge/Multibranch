node('Dev') {
    stage('ContinuousDownload_PB') 
    {
     git 'https://github.com/ArkLearnersEdge/maven.git'
    }
    stage('ContinuousBuild_PB') 
    {
     sh 'mvn package'
   }
}
