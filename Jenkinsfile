pipeline {
		agent {
	  docker {
	  	image 'ubuntu:latest'
	    args '''-v /home/ubuntu/jenkins/tools/:/tools/ \
	    		-v /captain/data/nginx-shared/www:/target \
	          -v /var/run/docker.sock:/var/run/docker.sock \
	          -v /usr/bin/docker:/usr/bin/docker \
	          --network sound-visualizer-testing-network \
	          -e CAPROVER_PASS=$CAPROVER_PASS
	          '''
	   }
	}

	stages {
		stage('build website') {
			steps {
				sh 'cd homepage; /tools/hugo'
			}
		}
		stage('publish') {
			steps {
				sh 'mv homepage/homepage/public/* /target/'
			}
		}
	}
}