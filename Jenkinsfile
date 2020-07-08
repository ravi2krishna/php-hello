

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                sh 'instances.sh'
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
