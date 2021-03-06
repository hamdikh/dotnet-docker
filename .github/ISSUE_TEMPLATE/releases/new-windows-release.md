# New Windows Release

Windows version: &lt;version&gt;

## Master Branch Tasks

1. - [ ] Ensure a ["New Windows Release" issue](https://github.com/dotnet/docker-tools/blob/.github/ISSUE_TEMPLATE/releases/new-windows-release.md) exists for docker-tools repo
1. - [ ] Copy the Dockerfiles of the most recent published Windows version for all supported .NET versions and place them in a version-specific folder under their respective variants (runtime, aspnet, sdk)
1. - [ ] Modify the Dockerfiles as appropriate for any specific changes related to the new Windows version
1. - [ ] Update [manifest.json](https://github.com/dotnet/dotnet-docker/blob/nightly/manifest.json) to reference the new set of Dockerfiles with the appropriate tags
1. - [ ] Update the [test data](https://github.com/dotnet/dotnet-docker/blob/nightly/tests/Microsoft.DotNet.Docker.Tests/TestData.cs) to include the new Windows version
1. - [ ] Update the [tags metadata templates](https://github.com/dotnet/dotnet-docker/tree/master/eng/mcr-tags-metadata-templates) to include the new Windows version
1. - [ ] Run the command to update the READMEs: `.\eng\readme-templates\Get-GeneratedReadmes.ps1`
1. - [ ] Run the command to update the image size baseline file: `.\tests\performance\Validate-ImageSize.ps1 -UpdateBaselines`
1. - [ ] Inspect generated changes for correctness
1. - [ ] Test the images
      1. - [ ] Create a local VM of the new Windows version
      1. - [ ] Clone this repo with the above changes onto the VM
      1. - [ ] Run `.\build-and-test.ps1 -OS nanoserver-<VERSION>` to build and test your changes
1. - [ ] Commit generated changes
1. - [ ] Create PR
1. - [ ] Get PR signoff
1. - [ ] Merge PR as part of the master branch [release process](dotnet-release.md) for the next .NET release
1. - [ ] Wait for automatically queued CI build to finish on [dotnet-docker-nightly pipeline](https://dev.azure.com/dnceng/internal/_build?definitionId=359) (internal MSFT link)
1. - [ ] Confirm images have been ingested by MCR
1. - [ ] Confirm READMEs have been updated in [Docker Hub](https://hub.docker.com/_/microsoft-dotnet-nightly)
1. - [ ] Create an announcement (example: [Nano Server, version 1909](https://github.com/dotnet/dotnet-docker/issues/1460))
1. - [ ] Update the samples to reference the new Windows version:
      - [ ] [Nano Server sample Dockerfiles](https://github.com/dotnet/dotnet-docker/tree/master/samples)
      - [ ] [manifest.samples.json](https://github.com/dotnet/dotnet-docker/blob/master/manifest.samples.json)

## Nightly Branch Tasks

- [ ] Merge these changes to the nightly branch as part of the nightly branch [release process](dotnet-release.md) for the next .NET release.
