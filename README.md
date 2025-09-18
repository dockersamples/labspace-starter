# Labspace starter

This repository is intended to server as a template to help bootstrap a new Labspace.

## Instructions

1. Create a new repository using this repo as the template ([docs here](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)).

    **NOTE:** After creating the repo, a GHA workflow will run to do some additional bootstrapping. The bootstrapping workflow file will be removed during bootstrapping.

2. Clone your newly created repo to your local machine

3. Start the local development mode:

    ```bash
    # On Mac/Linux
    CONTENT_PATH=$PWD docker compose -f oci://dockersamples/labspace-content-dev -f .labspace/compose.override.yaml up

    # On Windows with PowerShell
    $Env:CONTENT_PATH = (Get-Location).Path; docker compose -f oci://dockersamples/labspace-content-dev -f .labspace/compose.override.yaml up
    ```

4. Update the `labspace.yaml` with your Labspace's title and description

5. Write your Labspace! Being in dev mode, your changes should be visible in the interface without a restart. Feel free to edit either on your host machine or in the Labspace itself!

    Add any supporting application files or resources directly into the Labspace. This repo will be cloned into the Labspace at startup.

    Be sure to check out the [docs](https://github.com/dockersamples/labspace-infra/tree/main/docs) for additional information and guidelines.



### Setting up the deployment pipeline

The template repo contains a workflow file to make it easy to publish your Labspace.

1. Add GitHub Action Secrets in your new repo for the following:

    - `DOCKERHUB_USERNAME` - the username to authenticate to Docker Hub with
    - `DOCKERHUB_TOKEN` - a personal or organization access token to use for authentication

2. In the `.github/workflows/publish-labspace.yaml.temp` file, update the `DOCKERHUB_REPO` with the name of the Docker Hub repo you want to publish to.

3. Rename the workflow file to remove the `.temp` extension.

    ```bash
    mv .github/workflows/publish-labspace.yaml.temp .github/workflows/publish-labspace.yaml
    ```
