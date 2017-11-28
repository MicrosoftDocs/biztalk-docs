## Microsoft Open Source Code of Conduct
This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). See the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/), or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments. 

## Contribute to your documentation
We **want and encourage contributions** from our community (users, customers, partners) and Microsoft employees to improve your documentation. Here are some tips:

* **Minor updates**: If you are making minor updates, then find the article in this repository, and make your updates. Or, go to the article on [https://docs.microsoft.com/biztalk](https://docs.microsoft.com/biztalk), and select the **Edit** link. This opens the GitHub source for the article. Then, just use the GitHub UI within your web browser to make your updates. 

* **Major updates**: If you are making major updates, we recommend forking the repository (making a copy to your GitHub account), and make your edits within [VS Code](https://code.visualstudio.com/Download). You can then submit your changes to the Live branch, where they are reviewed, and then merged & published. 

* **MSFT Employees**: If you are a PFE, on the support team, program manager, or developer from the BizTalk or HIS product teams, then it's your job to contribute to or author technical articles. If you are making substantial changes to an existing article, adding or changing images, or contributing a new article, then we suggest to fork this repository, install Git Bash, a markdown editor ([VS Code](https://code.visualstudio.com/Download) is preferred), and learn some git commands. The [internal contributor's guide](https://review.docs.microsoft.com/help/contribute/?branch=master) provides the details to get started.

## Repo rules
When you update a topic, please: 

1. Make your changes to the **Live** branch. There may be other branches, but Live is the branch that is published to `docs.microsoft.com/biztalk`.

2. Change **ms.date** to the date you update the topic. Here's an example: 

    ```
    ms.date: "11/28/2017"
    ```

3. **Description** may be used for SEO. If it's missing a description, please add one. Here's an example: 

    ```
    title: Configure using Basic or Custom configuration | Microsoft Docs
    description: Steps to do a basic or custom configuration of BizTalk Server, and learn what happens with each configuration
    ```

4. Want some guidance or help for your pull request? Tag `@mandiohlinger` in your pull request, and I'll add my notes to the comments. 

## BizTalk repository structure

### \adapters-and-accelerators
Contains all the installation and conceptual documentation for the BizTalk Adapter Pack (BAP), HL7, RosettaNet, SWIFT, FileAct/Interact, and the WCF LOB Adapter SDK. It does not include the built-in or native adapters, such as FTP, or WCF-WebHTTP. These are included in *\core*.

### \core
Contains all the conceptual documentation, including getting started, tutorials, performance, the built-in adapters, B2B, and BAM. These topics typically apply to multiple BizTalk versions. 

### \dev-centers
Contains all the stand-alone topics at [https://docs.microsoft.com/biztalk](https://docs.microsoft.com/biztalk), including the community-written blogs.

### \esb-toolkit
Contains all the topics on the ESB Toolkit, including installation.

### \install-and-config-guides
Includes all the setup guides, including hardware and software requirements, what's new with the different BizTalk versions, the install steps, and the configuration steps. This folder contains version-specific topics, such as **Installing BizTalk Server 2016**, and so on.

### \technical-guides
Contains the performance guide, operations guide, white papers, and more. 

## Use markdown to format your topic
All the articles in this repository use GitHub-flavored markdown.  Here's a list of resources.

* [Markdown basics](https://help.github.com/articles/markdown-basics/)
* [Printable markdown cheatsheet](./contributor-guide/media/documents/markdown-cheatsheet.pdf?raw=true)
