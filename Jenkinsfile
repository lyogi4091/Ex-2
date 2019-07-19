node {
    stage('SCM'){
        git 'git@github.com:lyogi4091/Ex-2.git'
    stage('Building Docker image'){  
                sh 'sudo docker build -t ubuntu_image_remotely .';
                sh 'sudo docker run -it -d --name testcontainer_remote_ex2 -v /home/ciuser/Ex-2:/opt ubuntu_image_remotely';
        }
	stage ('Format check'){
	    try {
	        sh 'pycodestyle --ignore=E501 python_good.py';
		    echo 'python_good.py is in good format'
            }catch(x){
                println "python_good.py is in bad format"
               }
            try {
		    sh 'pycodestyle --ignore=E501 python_bad.py';
		    echo 'python_bad.py is in good format'
            }catch(x){
                println 'python_bad.py is in bad format'
               }
	}
    }
}
