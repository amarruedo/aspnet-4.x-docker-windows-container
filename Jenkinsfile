
node('windows'){

  deleteWorkspace()
  checkout scm
  def environment  = dockerExt.build "asp_net:build", "-f Dockerfile.build ."
  environment.inside () {

    stage("Prepare"){
      bat 'nuget restore'
    }

    stage("Build"){
      bat '"c:\\Program Files (x86)\\MSBuild\\14.0\\Bin\\MSBuild.exe" /p:Platform="Any CPU" /p:VisualStudioVersion=12.0 /p:VSToolsPath=c:\\MSBuild.Microsoft.VisualStudio.Web.targets.14.0.0.3\\tools\\VSToolsPath DockerDemo.sln'
    }

    stage("Clean"){
      //deleteWorkspace()
    }

  }
}
