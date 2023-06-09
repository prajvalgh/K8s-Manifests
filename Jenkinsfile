node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                      
                        sh "git config user.email prajvalgh12@gmail.com"
                        sh "git config user.name prajvalgh"
                      
                        sh "cat deployment.yaml"
                        sh "sed -i 's+prajvalgh/packages.*+prajvalgh/packages:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'By Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
			sh "git git remote set-url origin https://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@github.com/prajvalgh/K8s-Manifests.git"
                        sh "git push origin main" 
      }
    }
  }
}
}
