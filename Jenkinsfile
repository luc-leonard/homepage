pipeline {
		agent {
	  docker {
	  	image 'alpine:latest'
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
				sh 'ls -l /'
				sh 'ls -l /target'
				sh 'ls -l /tools'
				sh 'ls -l /real_root/'
				sh 'cp /tools/hugo /hugo'
				sh 'chmod 777 /hugo'
				sh 'ls -l /'
				sh 'cd homepage; /hugo'
			}
		}
		stage('publish') {
			steps {
				sh 'cp homepage/public /target'
			}
		}
	}
}