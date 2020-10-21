node {
    stage ('clone') {
        git branch: 'master', credentialsId: 'chhanz', url: 'git@gitlab.example.com:chhanz/cicd-httpd-source.git'
    }

    stage ('docker build') {
         sh ' docker build --tag sample-ci-httpd .'
    }
    
    stage ('run docker') {
         sh ' docker run -d -ti --name jenkins-ci -p 33333:80 sample-ci-httpd'
    }
    
    stage ('check httpd') {
         sh 'curl -s http://127.0.0.1:33333'
    }
    
    stage ('rm docker') {
         sh ' docker rm -f jenkins-ci'
    }

}
