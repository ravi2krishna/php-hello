

pipeline {
    agent any
    
    environment {
        SERVERS = sh(script: "sh instances.sh", returnStdout: true).trim()
    }
    
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                echo '${env.SERVERS}'
                //sh 'sh instances.sh'
            }
        }
        stage ('Deploy') {
        steps{
        sshagent(credentials : ['asg']) {
            
            sh 'ssh -o StrictHostKeyChecking=no ubuntu@54.196.254.168 uptime'
            sh 'ssh -v ubuntu@54.196.254.168'
            sh 'ssh -t -t ubuntu@54.196.254.168 -o StrictHostKeyChecking=no hostname'
            //sh 'scp ./source/filename user@hostname.com:/remotehost/target'
        }
    }
}
    }
}
