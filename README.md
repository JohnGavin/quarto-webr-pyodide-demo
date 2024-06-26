# Authoring Space with Continuous Deployment

[johngavin.github.io/quarto-webr-pyodide-demo](https://johngavin.github.io/quarto-webr-pyodide-demo)
[quarto-webr.qmd](quarto-webr.qmd#section1)
[quarto-pyodide.qmd](quarto-pyodide.qmd)
[about](about.qmd#section2)

> [!CLI] 
> 
> To build the website
> [johngavin.github.io/quarto-webr-pyodide-demo](https://johngavin.github.io/quarto-webr-pyodide-demo)
> # terminal in Rstudio in browser
> quarto preview
> quarto render 
> # R console in VSCode (not Rstudio)
> gert::git_commit_all('quarto render not quarto preview')
> gert::git_pull()
> gert::git_push()
> [.../actions/workflows/static.yml](https://github.com/JohnGavin/quarto-webr-pyodide-demo/actions/workflows/static.yml)

repo is  
+ example workflow for Quarto documents 
  + augmented by Quarto Extensions like
  + [`{quarto-webr}`](https://github.com/coatless/quarto-webr) and 
  + [`{quarto-pyodide}`](https://github.com/coatless-quarto/pyodide)

## Authoring Workspaces

We use 
[Development Containers (`devcontainers`)]
(https://containers.dev/) 
to create 
[two different authoring workspaces](.devcontainer/) 
that work with 
[GitHub Codespaces](https://github.com/features/codespaces). 
These authoring spaces are setup to immediately to modify 
+ projects without needing to install software 
  + (Quarto, RStudio or VS Code, and the extensions) 
  + on your local computer.
+ [`quarto-webr`](https://github.com/coatless/quarto-webr)
+ [`quarto-pyodide`](https://github.com/coatless-quarto/pyodide) 

> [!NOTE] 
> 
> Codespaces have 
> [upto 60 core hours + 15 GB free per month](https://github.com/features/codespaces#pricing).


### VS Code 

If you are comfortable with VS Code, you can try out the authoring space by clicking on the following button:

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/coatless-quarto/quarto-webr-pyodide-demo?devcontainer_path=.devcontainer%2Fvs-code%2Fdevcontainer.json)

### RStudio

RStudio Authoring Space requires a few more steps. 
You can access the space by clicking on:

[![Open RStudio Authoring Workspace in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/coatless-quarto/quarto-webr-pyodide-demo?devcontainer_path=.devcontainer%2Frstudio%2Fdevcontainer.json)

After the authoring space loads, 
click on the 
"Open in Browser" button 
in the lower right hand side to be taken into a new browser window with RStudio running: 

![Terminal tab with "Your application (RStudio) is running on" notification with "Open in Browser" button](images/vs-code-terminal-launch-rstudio-notification-closeup.png)

If you do not see the notification, please click on the "Ports" tab in the lower right hand side of VS Code and, then, find the "RStudio" label under Port column, press the globe under the "Forwarded Address" column next to "RStudio" to be taken into a web-based version of RStudio.

![Port tab showing the `RStudio` Process with the Globe Highlighted to "Open In Browser"](images/vs-code-port-tab-open-rstudio-globe.png)

If done successfully, you should see a new browser window with the familiar RStudio interface:

![Full RStudio authoring workspace](images/rstudio-authoring-workspace-launched.png)

From there, open the desired Quarto document by double clicking on it in the Files tab on the lower right hand side. Then, press the "Render" button. RStudio will then open a new tab with the rendered Quarto document. 

## Enabling GitHub Pages Deployment

> [!IMPORTANT]
> 
> This sections requires the repository to be cloned and/or forked to a personal copy for it work.

To enable deployment through GitHub Actions to GitHub Pages, please enable it on the repository by:

- Clicking on the repository's **Settings** page
- Selecting **Pages** on the left sidebar.
- Picking the **GitHub Actions** option in the **Source** drop-down under the Build and Deployment section.
- Ensuring that **Enforced HTTPS** is checked. 

[![Example annotation of the repository's Settings page for GitHub Actions deployment][1]][1]

This allows the GitHub Action in [`.github/workflows/publish-document.yml`](.github/workflows/publish-document.yml) to run each time a commit is made to the repository.

  [1]: images/enable-github-pages-via-actions.png