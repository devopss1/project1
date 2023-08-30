
pipeline{
			agent any
			// agent { label ‘jenkins2’ }

		//	tools{
				// MAVEN “M3”
		//	}

			stages{
					stage('checkout'){
							steps{
								//	git clone <url>
								echo "checkout from SCM"
								git 'https://github.com/devopss1/project1.git'
								}
					}
					stage('Build'){
							steps{
									// mvn package
									   echo "Build using maven"
									sh 'mvn package'
								}
					}
					stage('artifact upload'){
							steps{
									 echo "Upload to artifactory"
									nexusArtifactUploader artifacts: [[artifactId: 'project1', classifier: '', file: '/root/.jenkins/workspace/pipeline/target/project1.war', type: 'war']], credentialsId: 'daf2ab1e-1e5e-4760-be42-1f42a7b18c02', groupId: 'google', nexusUrl: '192.168.0.20:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'snapshots', version: '1.0-SNAPSHOT'
								}
					}
					stage('deploy'){
							steps{
								echo "Deploy to Prod env"	 							 
								sh 'cp /root/.jenkins/workspace/job01/target/project1.war /root/tomcat/apache-tomcat-9.0.78/webapps/'
								}
					}
	}
    
}
