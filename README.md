# PoI-CodeSpaces-GS
This repo is dedicated to empower your skills in the use of Codespaces, please fork this repo!

</header>


## Step 1: Create your first codespace and push code

_Welcome to this training! :wave:_

**What's the big deal about using a codespace for software development?** A codespace is a development environment that's hosted in the cloud. You can customize your project for GitHub Codespaces by committing configuration files to your repository (also known as configuration-as-code), which creates a repeatable codespace configuration for all users of your project. Each codespace you create is hosted by GitHub in a Docker container that runs on a virtual machine. You can choose the type of machine you want to use depending on the resources you need.

GitHub offers a range of features to help your development team customize a codespace to reach peak configuration and performance needs. For example, you can:

- Create a codespace from your repository.
- Push code from the codespace to your repository.
- Use VS Code to develop code.
- Customize the codespace with custom images.
- Manage the codespace.

To begin developing using GitHub Codespaces, you can create a codespace from a template or from any branch or commit in a repository. When you create a codespace from a template, you can start from a blank template or choose a template suitable for the work you're doing.

### :keyboard: Activity: Start a codespace

**We recommend opening another browser tab to work through the following activities so you can keep these instructions open for reference.**

1. Start from the landing page of your repository.
1. Click the green **Code** button located in the middle of the page.
1. Select the **Codespaces** tab in the box that pops up and then click the **Create codespace on main** button.

   > Wait about 2 minutes for the codespace to spin itself up.
   > **Note**: It's a virtual machine spinning up in the background.

1. Verify your codespace is running. The browser should contain a VS Code web-based editor and a terminal should be present such as the below:
   ![codespace1](https://user-images.githubusercontent.com/26442605/207355196-71aab43f-35a9-495b-bcfe-bf3773c2f1b3.png)

### :keyboard: Activity: Push code to your repository from the codespace

1. From inside the codespace in the VS Code explorer window, select the `index.html` file.
1. Replace the **h1** header with the below:

   ```html
   <h1>Hello from the codespace!</h1>
   ```

1. Save the file.
   > **Note**: The file should autosave.
1. Use the VS Code terminal to commit the file change by entering the following commit message:

   ```shell
   git commit -a -m "Adding hello from the codespace!"
   ```

1. Push the changes back to your repository. From the VS Code terminal, enter:

   ```shell
   git push
   ```

1. Your code has been pushed to your repository!
1. Switch back to the homepage of your repository and view the `index.html` to verify the new code was pushed to your repository

## Step 2: Add a custom image to your codespace!

_Nice work! :tada: You created your first codespace and pushed code using VS Code!_

You can configure the development container for a repository so that any codespace created for that repository will give you a tailored development environment, complete with all the tools and runtimes you need to work on a specific project.

**What are development containers?** Development containers, or dev containers, are Docker containers that are specifically configured to provide a fully featured development environment. Whenever you work in a codespace, you are using a dev container on a virtual machine.

A dev container file is a JSON file that lets you customize the default image that runs your codespace, VS code settings, run custom code, forward ports and much more!

Let's add a `devcontainer.json` file and add a custom image.

### :keyboard: Activity: Add a .devcontainer.json file to customize your codespace

1. Navigating back to your **Code** tab of your repository, click the **Add file** drop-down button, and then click `Create new file`.
1. Type or paste the following in the empty text field prompt to name your file.

   ```
   .devcontainer/devcontainer.json
   ```

1. In the body of the new **.devcontainer/devcontainer.json** file, add the following content:

   ```jsonc
   {
     // Name this configuration
     "name": "Codespace for Skills!",
     // Use the base codespace image
     "image": "mcr.microsoft.com/vscode/devcontainers/universal:latest",

     "remoteUser": "codespace",
     "overrideCommand": false
   }
   ```

1. Click **Commit changes** and then select **Commit changes directly to the `main` branch**.
1. Create a new codespace by navigating back to the **Code** tab of your repository.
1. Click the green **Code** button located in the middle of the page.
1. Click the **Codespaces** tab on the box that pops up.
1. Click the **Create codespace on main** button OR click the `+` sign on the tab. This will create a new codespace on the main branch. (Notice your other codespace listed here.)

   > Wait about **2 minutes** for the codespace to spin itself up.

1. Verify that your new codespace is is running, as you did previously.

   Note the image being used is the default image provided for GitHub Codespaces. It includes runtimes and tools for Python, Node.js, Docker, and more. See the full list here: https://aka.ms/ghcs-default-image. Your development team can use any custom image that has the necessary prerequisites installed. For more information, see [codespace image](https://aka.ms/configure-codespace).
## Step 3: Customize your codespace!

_Nice work! :tada: You created a codespace with a custom image!_

You can customize your codespace by adding VS code extensions, adding features, setting host requirements, and much more.

Let's customize some settings in the `devcontainer.json` file!

### :keyboard: Activity: Add customizations to the `devcontainer` file

1. Navigate to the `.devcontainer/devcontainer.json` file.
1. Add the following customizations to the body of the file before the last `}`.

   ```jsonc
    ,
    // Add the IDs of extensions you want installed when the container is created.
    "customizations": {
        "vscode": {
            "extensions": [
                "GitHub.copilot"
            ]
        },
        "codespaces": {
            "openFiles": [
                "codespace.md"
            ]
        }
    }
   ```

1. Click **Commit changes** and then select **Commit changes directly to the `main` branch**.
1. Create a new codespace by navigating to the landing page of your repository.
1. Click the **Code** button located in the middle of the page.
1. Click the **Codespaces** tab on the box that pops up.
1. Ensure the number of active codespaces does not reach the maximum (typically 2). For more information, see [understanding the codespace lifecycle](https://docs.github.com/en/codespaces/getting-started/understanding-the-codespace-lifecycle).

   > **Tip**: To stop an active codespace, click the **•••** next to **<span>&#x25cf;</span>Active** and select **Stop codespace** from the menu.
   
1. Click the **Create codespace on main** button.

   > Wait about **2 minutes** for the codespace to spin itself up.

1. Verify your codespace is running, as you did previously.
1. The `codespace.md` file should show up in the VS Code editor.
1. The `copilot` extension should show up in the VS Code extension list.

   This will add a VS Code extension as well as open a file on start up of the codespace.

Next lets add some code to run upon creation of the codespace!

### :keyboard: Activity: Execute code upon creation of the codespace

1. Edit the `.devcontainer/devcontainer.json` file.
1. Add the following postCreateCommand to the body of the file before the last `}`.

   ```jsonc
    ,
    "postCreateCommand": "echo '# Writing code upon codespace creation!'  >> codespace.md"
   ```

1. Click **Commit changes** and then select **Commit changes directly to the `main` branch**.
1. Create a new codespace by navigating to the landing page of your repository.
1. Click the **Code** button located in the middle of the page.
1. Click the **Codespaces** tab on the box that pops up.
1. Click the **Create codespace on main** button.

   > Wait about **2 minutes** for the codespace to spin itself up.

1. Verify your codespace is running, as you did previously.
1. Verify the `codespace.md` file now has the text `Writing code upon codespace creation!`.

## Step 4: Personalize your codespace!

_Nicely done customizing your codespace!_ :partying_face:

When using any development environment, customizing the settings and tools to your preferences and workflows is an important step. GitHub Codespaces offers two main ways of personalizing your codespace: `Settings Sync` with VS Code and `dotfiles`.

`Dotfiles` will be the focus of this activity.

**What are `dotfiles`?** Dotfiles are files and folders on Unix-like systems starting with . that control the configuration of applications and shells on your system. You can store and manage your dotfiles in a repository on GitHub.

Let's see how this works!

### :keyboard: Activity: Enable a `dotfile` for your codespace

1. Start from the landing page of your repository.
1. In the upper-right corner of any page, click your profile photo, and then click **Settings**.
1. In the **Code, planning, and automation** section of the sidebar, click **Codespaces**.
1. Under **Dotfiles**, select **Automatically install dotfiles** so that GitHub Codespaces automatically installs your dotfiles into every new codespace you create.
1. Click **Select repository** and then choose your current working repository as the repository from which to install dotfiles.

### :keyboard: Activity: Add a `dotfile` to your repository and run your codespace

1. Start from the landing page of your repository.
1. Click the **Code** button located in the middle of the page.
1. Click the **Codespaces** tab on the box that pops up.
1. Click the **Create codespace on main** button.

   > Wait about **2 minutes** for the codespace to spin itself up.

1. Verify your codespace is running. The browser should contain a VS Code web-based editor and a terminal should be present such as the below:

   ![codespace1](https://user-images.githubusercontent.com/26442605/207355196-71aab43f-35a9-495b-bcfe-bf3773c2f1b3.png)

1. From inside the codespace in the VS Code explorer window, create a new file `setup.sh`.
1. Enter the following code into the file:

   ```bash
   #!/bin/bash

   sudo apt-get update
   sudo apt-get install sl
   export PATH=$PATH:/usr/games
   ```

1. Save the file.
   > **Note**: The file should autosave.
1. Commit the file changes. From the VS Code terminal enter:

   ```shell
   git add setup.sh --chmod=+x
   git commit -m "Adding setup.sh from the codespace!"
   ```

1. Push the changes back to your repository. From the VS Code terminal, enter:

   ```shell
   git push
   ```

1. Switch back to the homepage of your repository and view the `setup.sh` to verify the new code was pushed to your repository.
1. Close the codespace web browser tab.
1. Click the **Create codespace on main** button.

   > Wait about **2 minutes** for the codespace to spin itself up.

1. Verify your codespace is running, as you did previously.
1. Verify the `setup.sh` file is present in your VS Code editor.

## Challenge: Practice what you learned today!

Now you are able to create codespaces for your projects.

Your next mission if you accept it is:

### Create a new codespace to create a full stack web app

Create a new codespace using a custom image, the codespace should allow to develop the following:
1. Rest APIs in Python
2. React SPAs
3. NodeJS code
4. All Components need to be containerized using docker
5. You must include VSCode Extension in order you can use GH Copilot, Bicep, extensions to make us easy to develop in python, react and NodeJS
6. Also the environment must be able to develop bicep files and execute Azure CLI commands

If you finish this challenge you will receive an special gift.

A successfull challenge will be considered if you can create and execute :
1. Simple container
2. Hello World Python app
3. Hello World NodeJS app
4. Hello World React app
5. A Successfull az login command

Tip: You can use devcontainer configuration from the GH portal, also GH Copilot is your friend! 

