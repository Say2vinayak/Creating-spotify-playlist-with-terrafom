# Creating Multiple Spotify Playlists Using Terraform

https://youtu.be/LjJLZRi_zGU

## Project Overview

This project involves using Terraform to create multiple Spotify playlists for different occasions like morning, evening, party night, etc. Terraform will be used to automate the creation and management of these playlists.

## Prerequisites

1. **Terraform Installed**: Ensure Terraform is installed on your machine.
2. **Docker Installed**: Make sure Docker is installed and running.
3. **Spotify Account**: You need a Spotify account (without premium access)
4. **Spotify Developer Account**: Register and create an application to get the Client ID and Client Secret.
5. **Spotify Provider for Terraform**: Install and configure the Spotify provider for Terraform.
6. **VS Code Editor**: Recommended for editing Terraform files.

## Steps to Complete the Project

### 1. Creating Terraform Code

Start by setting up your Terraform project.

1. Create a new directory for your Terraform project and navigate to it in your terminal.
2. Create a file named `main.tf`.

### 2. Define Provider

In `main.tf`, define the Spotify provider:

```
provider "spotify" {
  api_key = "?"
}

```

### 3. Need API Key

To interact with Spotify's API, you need a Client ID and Client Secret.

### 4. Start with App Creation

1. Go to the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard/).
2. Log in with your Spotify account.
3. Click on "Create an App".
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/84ad6f6a-681d-4a55-a9be-d328db326720/41729937-707e-480f-af79-b988b4f92aff/Untitled.png)
    
4. Fill in the required details and create the app.
    
    
    | Name | Description |
    | --- | --- |
    | My Playlist through Terraform | Create multiple Spotify playlists using Terraform. |
    - *Redirect URIs: [http://localhost:27228/spotify_callback](http://localhost:27228/spotify_callback**)

1. Click on Settings and note down the `Client ID` and `Client Secret`.
    
    https://developer.hashicorp.com/_next/image?url=https%3A%2F%2Fcontent.hashicorp.com%2Fapi%2Fassets%3Fproduct%3Dtutorials%26version%3Dmain%26asset%3Dpublic%252Fimg%252Fterraform%252Fdeveloper.spotify.com_dashboard_login-client-secret.png%26width%3D2584%26height%3D1176&w=3840&q=75&dpl=dpl_EJfEZ5oZYthY9Di2L7wZukaXMQv2
    

### 5. Enter Details

Create a file named `.env` to store your Spotify application's Client ID and Secret:

```
SPOTIFY_CLIENT_ID=<your_spotify_client_id>
SPOTIFY_CLIENT_SECRET=<your_spotify_client_secret>

```

### 6. Run the Spotify Auth App and Get the API Key

Make sure Docker Desktop is running, and start the authorization proxy server:

```
docker run --rm -it -p 27228:27228 --env-file ./.env ghcr.io/conradludgate/spotify-auth-proxy

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/84ad6f6a-681d-4a55-a9be-d328db326720/b3f4a8b1-3a7c-4837-b4f7-477d63f8652a/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/84ad6f6a-681d-4a55-a9be-d328db326720/e3320b06-8ac2-4a2b-a6dd-449746bc1c61/Untitled.png)

### You should get “Authorization Successful” Message.

8. Continue Creating Terraform Code

### 9. Initialize and Apply Terraform Configuration

1. Initialize the Terraform configuration:
    
    ```
    terraform init
    
    ```
    
2. Apply the Terraform configuration:
    
    ```
    terraform apply
    
    ```
    

### 11. Verify Playlists on Spotify

After applying the Terraform configuration, log in to your Spotify account and verify that the playlists have been created and populated with the specified tracks.

## Conclusion

By following these steps, you can automate the creation and management of multiple Spotify playlists using Terraform. This approach not only saves time but also ensures consistency across your playlists. Customize the playlists and tracks as per your preference to suit different occasions.
