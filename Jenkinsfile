pipeline{
	
	/*libraries{
lib 'shlib'
}
    agent any 
    tools{
        maven "mvn"
    }
	stages{
            stage('build'){
                steps{
                    build 'build'
                }
                }
           stage('deploy'){
               steps{
               //	withCredentials([usernamePassword(credentialsId: 'tomcat', passwordVariable: 'password', usernameVariable: 'username'),string(credentialsId: 'TOMCAT_URL', variable: 'tomcat_url')]){
		//sh 'curl http://18.216.136.124:8080//manager/text/undeploy?path=/bunny -u admin:admin'
		//sh 'curl -v -u admin:admin -T target/java-webapp.war http://18.216.136.124:8080//manager/text/deploy?path=/bunny'
			dep() 
		}
		}
             }*/
	
	agent {
	   docker { image 'sumavarshitha/java-maven-node' }
		//dockerfile true
	}
    stages {
	    stage('clone'){
		    steps{
			    //sh 'sudo rm -rf BT-assessment'
			    sh 'git clone https://github.com/SumaVarshitha/BT-assessment.git'
		    }}
        stage('build') {
            steps {
		    
                sh "mvn clean package"
            }
	}
	    stage('sonar'){
		    steps{
			     withSonarQubeEnv('sonar') {
				     sh 'mvn  sonar:sonar'}}
              }
    
    }
}
