# Azure_Download_GitHubNugetPackage.ado
Use this template to restore your NuGet packages or Download GitHub Nuget Packages using dotnet CLI in Azure Devops Pipeline.

## Parameters:

The pipeline requires the following parameters to be defined:


| Name  | Displayname | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | :-------------: | :-------------: | ------------- | :-------------: | ------------- |
| packageName | Package Name | string |  | | Required | Specifies the name of the package to download from GitHub |
| version | Package Version | string |  | | Required | Specifies the version of the package to download from GitHub |
| externalFeedCredentials | Credentials for feed from GitHub | string |  | | Optional | Required when selectOrConfig = config && command = restore. Specifies the credentials to use for external registry from GitHub |
| restoreDirectory | Destination directory Alias:packagesDirectory | string |  | | Optional | Use when command = restore. Specifies the folder where packages are installed. If no folder is specified, packages are restored into the default system working directory. |
--------------------------------------------------------------------------------------------------------------------------------------------------

These parameters provide multiple use case options for the template, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

You can directly call a particular template as per the requirement. for example: 

 ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/Azure_Download_GitHubNugetPackage.ado
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  steps:
  # passing the parameters
  - template: Azure_Download_GitHubNugetPackage.yml
    parameters:
      packageName: '${{parameters.packageName}}' . 
      version: '${{parameters.version}}' 
      externalFeedCredentials: '${{parameters.externalFeedCredentials}}' 
      restoreDirectory: '${{parameters.restoreDirectory}}' 
  ```
Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.
