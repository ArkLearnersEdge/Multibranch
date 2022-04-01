node('Dev') {
    stage('ContinuousDownload_Loans') 
    {
     git 'https://github.com/ArkLearnersEdge/maven.git'
    }
    stage('ContinuousBuild_Loans') 
    {
     sh 'mvn package'
   }
}
