node {
   def commit_id
   
   stage('Preparation') {
     checkout scm
     sh "git rev-parse --short HEAD > .git/commit-id"                        
     commit_id = readFile('.git/commit-id').trim()
   }
   
   stage('build test') {
     sh 'export NVM_DIR="$HOME/.nvm"
      [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
      [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"'
     
     sh 'npm install --only=dev'
     sh 'ls -lha'
     //nodejs(nodeJSInstallationName: 'nodejs') {
     //  sh 'npm install --only=dev'
     //}
     sh 'npm test'
   }
   
  /*
   stage('docker build/push') {
     docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
       def app = docker.build("wardviaene/docker-nodejs-demo:${commit_id}", '.').push()
     }
   }
   */
}
