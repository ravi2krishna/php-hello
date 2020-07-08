

pipeline {
    agent any
    
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                sh 'sh instances.sh > servers_list'
                sh 'cat servers_list'
                sh 'for word in $(cat servers_list); do echo $word; done'
            }
        }
        stage ('Deploy') {
        steps{
        sshagent(credentials : ['asg']) {
            sh 'sh instances.sh > servers_list'
            sh 'for word in $(cat servers_list); do echo $word; done'
            sh 'echo hello'
            sh 'for word in $(cat servers_list); do ssh -t -t ubuntu@$word -o StrictHostKeyChecking=no hostname; done'
            sh 'ssh -o StrictHostKeyChecking=no ubuntu@54.196.254.168 uptime'
            sh 'ssh -v ubuntu@54.196.254.168'
            //sh 'ssh -t -t ubuntu@54.196.254.168 -o StrictHostKeyChecking=no hostname'
            //sh 'scp ./source/filename user@hostname.com:/remotehost/target'
        }
    }
}
    }
}
