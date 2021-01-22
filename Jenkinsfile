pipeline {
	agent {
	  docker {
	  	image 'ubuntu'
	    args '''
	          -v /var/run/docker.sock:/var/run/docker.sock \
	          -v /usr/bin/docker:/usr/bin/docker \
	          -v /captain/data/nginx-shared/www /target \
	          -v /tools:/tools/
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