pipeline{
			agent{
				label{
					label 'built-in'
					customWorkspace '/mnt/jenkins/'
				}
			}
		stages{
				stage ('Installing git'){
										
										steps{
												sh " yum install git -y"
												sh " rm -rf *"
												sh "git clone https://github.com/abhilash0326/game-of-life.git"
												
										}
					}
				stage ('building .war file'){
										steps {
												dir ('/mnt/jenkins/game-of-life/'){
													sh "rm -rf /root/.m2"
													sh "rm -rf /mnt/jenkins/game-of-life/target"
													sh "mvn clean install"
													
												}
										}
					
					}
				stage ('installing dokcer'){
										steps{
												sh "yum install docker -y"
												sh "systemctl start docker"
										}
					}
				stage ('deployment of gameoflife'){
										steps{
												sh "docker build -t gol:1 /mnt/docker/"
												sh " docker run -itdp 8080:80 gol:1 "
										}
					}
		}
		
		
}
