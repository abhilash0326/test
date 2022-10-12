pipeline{
			agent{
				label{
					label 'build-in'
					customWorkspace '/mnt/jenkins/'
				}
			}
		stages{
				stage ('Installing git'){
										
										steps{
												sh " yum install git -y"
												sh "git clone https://github.com/abhilash0326/game-of-life.git"
												
										}
					}
				stage ('building .war file'){
										steps {
												dir ('/mnt/jenkins/game-of-life/'){
													steps{
													sh "mvn clean install"
													}
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
