node {
    stage('chekout') {
        git 'https://github.com/abinassahoo/JunitExample.git'
     mvnHome = tool 'M3'
        }
        
    stage('test') {
        
        sh "'${mvnHome}/bin/mvn'  clean test"
    }
    stage('push to docker') {
        
        sh "'${mvnHome}/bin/mvn' package"
        def image = docker.build ('abinassahoo/myapp')
        docker.withRegistry("https://registry.hub.docker.com", "docker") {
        image.push()
    }
    stage('publish Result') {
        
        step([$class: 'JUnitResultArchiver', testResults: 'target/surefire-reports/*.xml'])
    }

  // stage('Results') {
    //  junit '**/target/surefire-reports/*.xml'
    //  archive 'target/*.war'
   //}
}
