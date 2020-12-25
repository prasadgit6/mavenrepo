pipeline{
agent { label 'Devslave' }
stages{

stage("checkout"){
steps{
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'd28b003b-a74d-4b77-9d3e-cd221a676822', url: 'https://github.com/prasadgit6/mavenrepo.git']]])
     }
                  }
stage("build"){
steps{
sh "mvn package"
      }

              } 
              
stage("sonar"){

steps{
withSonarQubeEnv('Sonarqube'){

sh "mvn sonar:sonar"
                         }
      }
                          
              } 
 
 stage("nexus"){
steps{
sh "mvn deploy"
      }

              } 
              
               stage("deploy"){
steps{
sh "scp /root/workspace/jenkin1/target/studentapp-2.5-SNAPSHOT.war 52.66.119.232:/var/lib/tomcat/webapps"
      }

              }
      }
        }
