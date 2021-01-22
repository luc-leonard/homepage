pipeline {
	agent {
	  docker {
	  	image 'klakegg/hugo:0.80.0-ext-alpine'
	    args '''
	          -v /var/run/docker.sock:/var/run/docker.sock \
	          -v /usr/bin/docker:/usr/bin/docker \
	          -v /captain/data/nginx-shared/www /target
	          --network sound-visualizer-testing-network \
	          -e CAPROVER_PASS=$CAPROVER_PASS
	          '''
	   }
	}

	stages {
		stage('build website') {
			steps {
				sh 'cd homepage; hugo'
			}
		}
		stage('publish') {
			steps {
				sh 'cp homepage/public /target'
			}
		}
	}
}