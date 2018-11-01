def genericSh(cmd) {
  if (isUnix()) {
    sh cmd
  }
  else {
    bat cmd
  }
}

node {
  stage('Checkout') {
    checkout scm
  }

  stage('Build') {
    azureIoTEdgePush dockerRegistryType: 'acr', acrName: 'zhiqing' , bypassModules: '', azureCredentialId: 'azuresp', resourceGroup: 'zhiqing', rootPath: './'
  }

  stage('Deploy') {
    azureIoTEdgeDeploy azureCredentialsId: 'azuresp', deploymentId: 'jenkins-deploy', deploymentType: 'single', deviceId: 'edge', iothubName: 'anotheriothub', priority: '0', resourceGroup: 'devkit-happypath-demo', rootPath: './', targetCondition: ''
  }
}