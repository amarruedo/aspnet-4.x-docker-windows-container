
node('windows'){
  
  deleteWorkspace()
  git changelog: false, poll: false, url: 'https://github.com/amarruedo/aspnet-4.x-docker-windows-container.git'
  def environment  = docker.build "asp_net:build", "-f Dockerfile.build ."
  environment.inside ("${buildParams.dockerEnvs} ${dockerParams.runArgs}") {

    stage("Prepare"){
      bat 'nuget restore'
    }

    stage("Build"){
      bat '"c:\Program Files (x86)\MSBuild\14.0\Bin\MSBuild.exe" /p:Platform="Any CPU" /p:VisualStudioVersion=12.0 /p:VSToolsPath=c:\MSBuild.Microsoft.VisualStudio.Web.targets.14.0.0.3\tools\VSToolsPath DockerDemo.sln'
    }

    stage("Clean"){
      deleteWorkspace()
    }

  }
}
