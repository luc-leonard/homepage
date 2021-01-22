pipeline {
		agent {
	  docker {
	  	image 'python:3.8-buster'
	    args '''-v $HOME/.pip:/pip-cache \
	    		-e _IN_DOCKER=1 \
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
				sh 'cp homepage/public /target'
			}
		}
	}
}