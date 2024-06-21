# Repositories

[**Home**](./readme.md) | [**Previous**](./setup.md) | [**Next**](./issues.md)

There are two ways that you can setup a local git project:

* Cloning an existing repository to your local environment
* Creating a new project and connecting it to a new remote repository

The sections that follow will walk you through both processes.

> For a deep dive on repositories, see the [**References**](#references) section below.

## Cloning a Repository

The simplest method of setting up a local git project is to clone an existing repository from a remote source. All you need is the [**remote repository URL**](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#about-remote-repositories) and a configured git environment (see [**Setup**](./setup.md) for details).

> In order to contribute to a repository, you must have contributor permissions. For details on contributing to open source repositories, see [**Fork a repository**](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) in the GitHub docs.

The following will clone this `dev-workflow` GitHub repository:

```pwsh
# clone with SSH
C:\{path}> git clone git@work.github.com:s2va/dev-workflow.git

# output
Cloning into 'dev-workflow'...
remote: Enumerating objects: 26, done.
remote: Counting objects: 100% (26/26), done.
remote: Compressing objects: 100% (19/19), done.
remote: Total 26 (delta 6), reused 25 (delta 5), pack-reused 0
Receiving objects: 100% (26/26), 5.20 KiB | 1.30 MiB/s, done.
Resolving deltas: 100% (6/6), done.
```

Verify the repository contents have been cloned:

```pwsh
C:\{path}> ls .\dev-workflow\

# output

    Directory: C:\{path}\dev-workflow

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/14/2024    14:12             90 branches.md
-a---           6/14/2024    14:12             61 git-flow.md
-a---           6/14/2024    14:12             87 issues.md
-a---           6/14/2024    14:12             90 markdown.md
-a---           6/14/2024    14:12             83 projects.md
-a---           6/14/2024    14:12             90 pull-requests.md
-a---           6/14/2024    14:12            890 readme.md
-a---           6/14/2024    14:12             84 repositories.md
-a---           6/14/2024    14:12           6378 setup.md
```

## Creating a New Repository

The process of creating a local source controlled project and connecting it to a remote repository is a bit more complicated. The sections that follow will walk through the process.

> Note that you could just as easily start from the **Remote Setup** section and follow up with the **Local Setup** section after. The order is interchangeable.

### Local Setup

From a terminal, initialize a simple directory with a `readme.md` file:

```pwsh
C:\{path}> mkdir new-project
C:\{path}> new-item .\new-project\readme.md
```

Open the `new-project` directory in Visual Studio Code and provide `readme.md` with some content:

![readme](https://github.com/JaimeStill/JaimeStill/assets/14102723/6e92ec13-5255-4768-b866-d7b0d725de67)

```pwsh
C:\{path}> code new-project
```

Initialize git source control by executing the following from a terminal pointed to the `new-project` directory:

```pwsh
C:\{path}\new-project> git init

# output
Initialized empty Git repository in C:/{path}/new-project/.git/
```

Add, also referred to as *tracking* or *staging*, all of the files in the `new-project` directory:

```pwsh
# don't forget the .
C:\{path}\new-project> git add .
```

Create a first commit:

```pwsh
C:\{path}\new-project> git commit -m "initial"

# output
[main (root-commit) 9a4e772] initial
 1 file changed, 3 insertions(+)
 create mode 100644 readme.md
```

Leave this terminal open to complete the steps in the upcoming [**Connecting Local to Remote**](#connecting-local-to-remote) section.

### Remote Setup

The steps above setup the project for local source control, but what you really want is to a legitimate source control platform. To start, login to GitHub and navigate to [**Create a new repository**](https://github.com/new).

Select an **Owner**, provide a **Repository name**, and optionally provide a **Description**:

![new-repo](https://github.com/JaimeStill/JaimeStill/assets/14102723/94ad49ad-fc4c-4b2d-b4ab-af19236dc926)

Once you these options have been properly set, click **Create repository**. You will be routed to the empty repository home:

![repo-home](https://github.com/JaimeStill/JaimeStill/assets/14102723/b5ca4966-2c77-4f0a-8eef-c9aa91a57c69)

### Connecting Local to Remote

If you closed the terminal used for the [**Local Setup**](#local-setup) section above, open a terminal pointed to the `new-project` directory and execute the following:

> Be sure to adjust the SSH URL to match your key configuration. In this case, I'm using `@work.github.com` instead of `@github.com`

```pwsh
C:\{path}\new-project> git remote add origin git@work.github.com:s2va/new-project.git
```

Push your committed files up to the remote repository:

```pwsh
C:\{path}\new-project> git push -u origin main

# output
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 273 bytes | 273.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To work.github.com:s2va/new-project.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

If you refresh the repository in the browser, you can see that your remote repository is now up to date with your local project:

![repo-connected](https://github.com/JaimeStill/JaimeStill/assets/14102723/d6f296a1-f9a6-4546-ac48-19d52c3dbd42)

### Configure Multiple Push Targets

If you're working on a repository that is not proprietary to your organization, i.e. - an R&D project to develop a new capability, you can configure multiple push targets.

If you look at the current origin configuration, you will see that there is currently only one *Push URL*:

```pwsh
C:\{path}\new-project> git remote show origin

# output
git remote show origin
* remote origin
  Fetch URL: git@work.github.com:s2va/new-project.git
  Push  URL: git@work.github.com:s2va/new-project.git
  HEAD branch: main
  Remote branch:
    main tracked
  Local branch configured for 'git pull':
    main merges with remote main
  Local ref configured for 'git push':
    main pushes to main (up to date)
```

If you create a repository on your personal GitHub account, you can have all pushes target both the work repository and your personal repository. To do so, you need to configure multiple push URLs.

First, because the project is currently configured with the work Push URL, you need to configure the personal repository as a Push URL:

```pwsh
C:\{path}\new-project> git remote set-url origin --add --push git@github.com:JaimeStill/new-project.git
```

Now, the first time you add a push URL in this way, it overwrites the initial push URL. You can verify this by showing the *origin* remote source:

```pwsh
C:\{path}\new-project> git remote show origin

# output
* remote origin
  Fetch URL: git@work.github.com:s2va/new-project.git
  Push  URL: git@github.com:JaimeStill/new-project.git
  HEAD branch: main
  Remote branch:
    main tracked
  Local branch configured for 'git pull':
    main merges with remote main
  Local ref configured for 'git push':
    main pushes to main (up to date)
```

If you specify the remote repository again using the same command, both URLs will be properly registered as push URLs:

```pwsh
C:\{path}\new-project> git remote set-url origin --add --push git@work.github.com:s2va/new-project.git
```

Confirm that both push URLs are configured:

```pwsh
C:\{path}\new-project> git remote show origin

# output
* remote origin
  Fetch URL: git@work.github.com:s2va/new-project.git
  Push  URL: git@github.com:JaimeStill/new-project.git
  Push  URL: git@work.github.com:s2va/new-project.git
  HEAD branch: main
  Remote branch:
    main tracked
  Local branch configured for 'git pull':
    main merges with remote main
  Local ref configured for 'git push':
    main pushes to main (up to date)
```

If you perform a push, you will see that git uses both push URLs:

```pwsh
# -u origin main needed for new push URL
C:\{path}\new-project> git push -u origin main

# output
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 273 bytes | 273.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To github.com:JaimeStill/new-project.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
branch 'main' set up to track 'origin/main'.
Everything up-to-date
```

In the above output, git pushes the files to the new personal github repository configured as a push URL. After that, it confirms that the remote work repository is still up to date.

### Using .gitgnore to Exclude Artifacts

There will often be times when there are sections of your project that you do not want included in source control. Some examples include dependency caches, large binary files, build artifacts, and many more.

> The example that follows is an extremely simplified demonstration of what .gitignore can actually do. Read [**.gitignore**](https://git-scm.com/docs/gitignore) and [**Ignoring files**](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files) for a more comprehensive description.

> In the example that follows, I will add a simple hello world CLI app using the [**.NET SDK**](https://dotnet.microsoft.com/en-us/download).

Open the `new-project` repo in VS Code and, from the terminal, initialize a new .NET console app:

```pwsh
C:\{path}\new-project> dotnet new console -n App.Cli

# output
The template "Console App" was created successfully.

Processing post-creation actions...
Restoring C:\{path}\new-project\App.Cli\App.Cli.csproj:
  Determining projects to restore...
  Restored C:\{path}\new-project\App.Cli\App.Cli.csproj (in 60 ms).
Restore succeeded.
```

When working with .NET projects, the restore and build commands generate `bin` and `obj` directories with cached dependencies and build artifacts. These will initially show up as being tracked by git:

![before-gitignore](https://github.com/JaimeStill/JaimeStill/assets/14102723/ab8f16c7-4b1d-4c81-ad8c-b18909ea87f0)

You do not want those to be tracked by git. To prevent that, create a `.gitignore` file in the root of the `new-project` workspace and give it the following values:

```gitignore
bin
obj
```

Once the file is saved, you can see the `bin` and `obj` directories are no longer tracked by git:

![after-gitignore](https://github.com/JaimeStill/JaimeStill/assets/14102723/220074c8-cdd3-44ce-9f64-8781e28a7834)

### Updating Remote from Local

All you need to do to update the remote repositories is:

Stage the current changes:

```pwsh
C:\{path}\new-project> git add .
```

Commit the changes locally:

```pwsh
C:\{path}\new-project> git commit -m "add CLI app"

# output
[main 2eb09d1] add CLI app
 3 files changed, 14 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 App.Cli/App.Cli.csproj
 create mode 100644 App.Cli/Program.cs
```

Push the changes to the configured Push URLs:

> Because both Push URLs have connected a local branch to a remote branch for tracking, you do not have to execute `git push -u origin main`. You can simply execute `git push` on this branch.

```pwsh
C:\{path}\new-project> git push

# output
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (6/6), 685 bytes | 342.00 KiB/s, done.
Total 6 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To github.com:JaimeStill/new-project.git
   9a4e772..2eb09d1  main -> main
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (6/6), 685 bytes | 342.00 KiB/s, done.
Total 6 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To work.github.com:s2va/new-project.git
   9a4e772..2eb09d1  main -> main
```

You can see in the output above that both personal and work repositories are updated with the latest committed changes:

**Personal Repository**

![update-personal](https://github.com/JaimeStill/JaimeStill/assets/14102723/9d2363fd-ed36-459b-9650-7880add4be02)

**Work Repository**

![update-work](https://github.com/JaimeStill/JaimeStill/assets/14102723/8218642f-504d-424f-80d7-4c159a312711)

## References

* [GitHub Repositories](https://docs.github.com/en/repositories/creating-and-managing-repositories/about-repositories)

[**Home**](./readme.md) | [**Previous**](./setup.md) | [**Next**](./issues.md)