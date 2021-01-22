pipeline {
		agent {
	  docker {
	  	image 'alpine:latest'
	    args '''-v /tools:/tools \
	    		-v /real_root/captain/data/nginx-shared/www:/target \
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
				sh 'ls -l /'
				sh 'ls -l /tools'
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