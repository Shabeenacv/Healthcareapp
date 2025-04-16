pipeline {
  agent any

  stages {
    stage('checkoutcode') {
      steps {
        git(url: 'https://github.com/Shabeenacv/Healthcareapp.git', branch: 'main')
      }
    }

    stage('Deploy to EC2') {
      steps {
        sshagent(['your-ec2-ssh-key-id']) {
          sh '''
          ssh -o StrictHostKeyChecking=no ec2-user@34.235.140.161 << EOF
            cd /var/www/html/Healthcareapp
            git pull origin main
            sudo systemctl restart httpd
          EOF
          '''
        }
      }
    }
  }
}
