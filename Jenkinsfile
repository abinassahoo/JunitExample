node {
    stage('chekout') {
        git 'https://github.com/abinassahoo/JunitExample.git'
     mvnHome = tool 'M3'
        }
        
    stage('test') {
        
        sh "'${mvnHome}/bin/mvn'  clean test"
    }
    stage('package') {
        
        sh "'${mvnHome}/bin/mvn' test"
    }
    stage('publish Result') {
        
        step([$class: 'JUnitResultArchiver', testResults: 'target/surefire-reports/*.xml'])
    }

   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.war'
   }
}
