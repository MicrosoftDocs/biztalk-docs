---
title: Step 2 - Create VSTS token and install agent
description: Create the VSTS security access token, clone your VSTS project into Visual Studio, and install the build agent to automate deployment of your BizTalk Server projects
ms.custom: ""
ms.date: "09/20/2022"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# Step 2: Create the token & install the agent

A personal access token (PAT) is created in Visual Studio Team Services. This token is your password, and is used by the VSTS build agent to authenticate. The token is only shown when you create it. After that, it isn't shown anymore. So once you create it, save it to another file in a remember-able location. 

More info on PAT at [Authenticate access with personal access tokens for VSTS and TFS](/vsts/accounts/use-personal-access-tokens-to-authenticate). 

After you create the token, you install the build agent, and configure it to use this token. 

## Before you begin

Complete [Step 1 - Add Application project and update json](feature-pack-add-application-project.md).

## Sign into Azure DevOps, and create the token

1. Go to [https://app.vsaex.visualstudio.com/go/profile](https://app.vsaex.visualstudio.com/go/profile), and sign-in with your work or school account. After you sign in, your VSTS account is listed. In the following example, the account is `dev.azure.com/v-vabi`:

    :::image type="content" source="./media/feature-pack-create-vsts-token/team-services-accounts.png" alt-text="Sign in to the Azure DevOps account, and see your account in the list.":::

    If you don’t have an account, select **Create new account**, and enter a name. To manage your code, choose your personal preference between **Git** or **Team Foundation Version Control**. When finished, your new account is created, and a site similar to `https://dev.azure.com/v-vabi/BizTalkVSTS` opens:  

    :::image type="content" source="./media/feature-pack-create-vsts-token/git-or-team-foundation.png" alt-text="Select Git or Team Foundation Version Control to host your Azure DevOps projects.":::

2. Open your DevOps account (`https://dev.azure.com/v-vabi/`). Select your icon in the top second right-side corner, and select **User settings** > **Personal access tokens**:

    :::image type="content" source="./media/feature-pack-create-vsts-token/azure-devops-personal-access-token.png" alt-text="Open your account personal access token security in Azure DevOps.":::

3. All the personal access tokens are shown.

    :::image type="content" source="./media/feature-pack-create-vsts-token/agent-pools-read-manage.png" alt-text="See all the personal access tokens in your account in Azure DevOps.":::

    > [!IMPORTANT]
    > You must know the access token. If you don’t, and didn’t note it anywhere, it cannot be retrieved. In this situation, create a new agent.

    If you don’t have an existing agent, select **Add**, enter a description, set the expiration date, and select your account. In **Selected scopes**, select **Agent Pools (read, manage)**: 

    :::image type="content" source="./media/feature-pack-create-vsts-token/vsts-new-build-agent.png" alt-text="Create a new read and manage agent in your Azure DevOps account":::

    Select **Create Token**. **Note the token value; you need in future steps.**

4. Select **Repos** > **Clone in Visual Studio**:  

    :::image type="content" source="./media/feature-pack-create-vsts-token/azure-devops-select-repo.png" alt-text="Select code when cloning your Azure DevOps project into Visual Studio.":::

    :::image type="content" source="./media/feature-pack-create-vsts-token/vsts-clone-in-visual-studio.png" alt-text="Select clone in Visual Studio for Azure DevOps.":::

5. Visual Studio opens. Within Visual Studio, open your BizTalk solution.

## Install the Build Agent

> [!NOTE]
> The build agent is installed on the BizTalk development computer. If using deployment groups, the build agent is installed on all the BizTalk servers you want to deploy to. Also, use these same steps to add a build computer, which might be different than the BizTalk development computer.
> 
> Optionally, you can build BizTalk projects using the Azure Pipelines agent pool, instead of the Build Agent. To use the Azure Pipelines agent pool, skip this section, and go to [Step 3: Create the build definition](feature-pack-add-build-release-definitions.md).

The following steps show you how to install the build agent on a single computer. For details on using deployment groups, see [Deployment groups](/vsts/build-release/concepts/definitions/release/deployment-groups/index).

1. Open your Azure DevOps account and project, which is something like `https://dev.azure.com/v-vabi/BizTalkVSTS`. Select the project settings icon, and select **Agent Pools**:

    :::image type="content" source="./media/feature-pack-create-vsts-token/azure-devops-settings-agent-queues.png" alt-text="In Azure DevOps, go to settings, agent queues to select agent pools.":::

2. Select the **Default** agent > **New Agent** **Download**. Save the file to your **Downloads** folders.

3. The install steps automatically open. Follow those steps for the most up-to-date details. Here is some guidance:

    1. Open Windows PowerShell as Administrator.
    2. To create the agent, enter:

        ```powershell
        PS C:\> mkdir agent ; cd agent  

        PS C:\agent> Add-Type -AssemblyName System.IO.Compression.FileSystem ; [System.IO.Compression.ZipFile]::ExtractToDirectory("$HOME\Downloads\vsts-agent-win7-x64-2.124.0.zip", "$PWD")
       ```

        The vsts-agent file version changes. So follow the VSTS install steps for specific details. After you hit enter, it may take a couple of minutes for the prompt to return. 

    3. To configure the agent, enter: 

        ```powershell
        PS C:\agent> .\config.cmd
        ```

    4. Enter the following details:

        - **Server URL**: Enter `https://{your-account}.visualstudio.com`.
        - **Authentication Type**: Enter `PAT`.
        - **Personal access token**: Paste your Azure DevOps token.
        - **Agent pool**: Enter for the default.
        - **Agent name**: Enter for the default.
        - **Replace**: Only displays if you have an existing agent.
        - **Work folder**: Enter for the default.
        - **Run agent as a service**: Enter `Y`.
        - **User account**: This value is up to you, but you may run into a permissions issue. Consider entering your current logged-on account, which is a local admin.

    5. When finished, your PowerShell window looks like the following:

        :::image type="content" source="./media/feature-pack-create-vsts-token/azure-devops-agent-powershell-install.png" alt-text="Agent install completes using PowerShell in Azure DevOps.":::

4. Open services.msc and locate the new service **Azure Pipeline Agent**. It should be running.

    If the service fails to start, [remove and re-configure an agent](/vsts/build-release/actions/agents/v2-windows) using an account with more privileges.

## What you did

You signed into your Azure DevOps account, and created a security token. This security token is like a password, and gives you access to your Azure DevOps project. It's only shown once, so be sure you saved it. You also cloned your Azure DevOps project into Visual Studio, and created an agent that runs as a service on your BizTalk development computer. This agent uses the security token.

## Next steps

[Step 3: Create the build definition](feature-pack-add-build-release-definitions.md)  
[Step 4: Create the release definition](azure-devops-add-release-definition.md)  
[Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md)