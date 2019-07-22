node {
    stage('Building Docker image'){
        checkout scm
        sh 'sudo docker build -t ubuntu_image_remotely .'
        sh 'sudo docker run -it -d --name testcontainer_remote -v /home/ciuser/Ex-2:/opt ubuntu_image_remotely'
    stage ('Format Check'){
        try{
            sh 'sudo docker exec testcontainer_remote pycodestyle --ignore=E501 /opt/python_good.py'
            println "python_good.py is already in good format "
            }catch(x){
                println "python_good.py is in good format. "
                }
        try{
            sh 'sudo docker exec testcontainer_remote pycodestyle --ignore=E501 /opt/python_bad.py'
            println "python_bad.py is already in good format"
            }catch(x){
                println "python_bad.py is in bad format."
                }
    }

        }
}
