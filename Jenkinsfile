node{
   stage('SCM Checkout'){
     git 'https://github.com/tirth95/JenkinsWar'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Deploy to Tomcat'){
      
      sshagent(['tomcat']) {
    sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.23.154:/apps/tomcat/apache-tomcat-9.0.21/webapps/' 
     } 
   }
   
}
