# Issues

[**Home**](./readme.md) | [**Previous**](./repositories.md) | [**Next**](./projects.md)

GitHub Issues are used to track ideas, feedback, tasks, or bugs for work on GitHub.

> For a deep dive on Issues, see the [**References**](#references) section below.

Issues contain the following properties:

Property | Description
---------|------------
Title | Concise headline indicating the intent of the issue.
Description | The details of the issue, provided in [**markdown format**](https://docs.github.com/en/get-started/writing-on-github).
Assignees | Users assigned to action the issue.
Labels | Categorical tags associated to an issue that facilitate issue organization.
Projects | The [**GitHub Projects**](https://docs.github.com/en/issues/planning-and-tracking-with-projects) the issue is associated with.
Milestone | The [**development milestone**](https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work/about-milestones) the issue is associated with.
Development | The [**branches**](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository) and [**pull requests**](https://docs.github.com/en/pull-requests) linked to the issue.

When creating an issue, the **Title** and **Description** are minimally required. The remaining properties can be set throughout the lifecycle of the issue.

All issues for a repository can be viewed with the URL `github.com/<org-or-user>/<repository>/issues`. New issues can be submitted through the `github.com/<org-or-user>/<repository>/issues/new` URL.

**Example Issue**

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/1e5e76ec-2e5a-45a7-b750-0376464f29d8)

In addition to text, you can [**attach files**](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/attaching-files) to issues and pull requests. This is particularly useful as you can paste images captured in the clipboard (i.e. - through the <kbd>Ctrl + Shift + s</kbd> snipping tool on Windows), and GitHub will upload and return a URL where the image can be referenced.

**URL Generated From Pasted Image**

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/78462e7a-2f9b-43c8-839e-0622dbcd95e5)

## Labels

Labels are used to provide structure and organization to issues. They can be viewed and configured at the URL `github.com/<org-or-user>/<repository>/labels`.

**Default Labels**

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/cf549596-ad68-4197-a3e4-98f9dd696f4c)

You can restructure labels however you want to suit the needs of your project.

## Milestones

Milestones are used to track progress on groups of issues or pull requests in a repository. They can be viewed and configured at the URL `github.com/<org-or-user>/<repository>/milestones`.

A milestone consists of:

* A title
* A due date
* A description (supports [markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) syntax).

**Example Milestones View**

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/39e46584-a6cb-46d4-86cc-09567568648a)

**Example Milestone with Issues**

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/920b28cc-5c6f-4a6a-9736-c849663119b1)

## Templates

You can define [**issue templates**](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository) to help standardize the structure and requested content of your issues. The templates defined by a repository can be viewed and configured at the URL `github.com/<org-org-user>/<repository>/issues/templates/edit`.

Alternatively, you can manually specify templates in your repository code base. Any templates applied to a repository will be stored as markdown files in the `.github/ISSUE_TEMPLATE/` directory at the root fo the repository. If you want to customize the order in which the issues appear when creating a new issue, prefix the markdown file name with a number. For instance:

* `1-task.md`
* `2-feature_request.md`
* `3-bug_report.md`

When creating issues as tasks, the structure of the task should always capture:

* The title with an overview of the task defined underneath it.
* The requirements of the task, broken down into measurable metrics.
* The end state of the task, capturing the expected outcome of completing the task.
* The check in date, used to set a point in time where blockers can be determined and progress can be analyzed.

**GUI Task Template**

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/51dd67a0-1750-456a-a8c2-e53a617019ed)

**Manual Task Template**

> Defined at `.github/ISSUE_TEMPLATE/1-task.md`.

```md
---
name: Task
about: Define the parameters of a self-contained work task.
title: ''
labels: ''
assignees: ''

---

# Title
Provide an overview of the task.

## Requirements
Break down the requirements of the task into measurable metrics.

## End State
Define the expected outcome of completing the task.

## Check In
A soft due date to analyze progress and determine blockers.
```

In addition to the name, description, and content, you can also specify default behaviors such as:

* A default issue title
* The labels to automatically apply to the issue
* The assignees to automatically apply to the issue

For example, `2-feature-request.md` automatically applies the **request** label to issues generated from the template:

```md
---
name: Feature request
about: Suggest an idea for this project
title: ''
labels: 'request'
assignees: ''

---

# Title
A clear and concise description of what the problem is. Ex. I'm always frustrated when [...]

## Solution
A clear and concise description of what you want to happen.

## Alternatives
A clear and concise description of any alternative solutions or features you've considered.

## Additional Context
Add any other context or screenshots about the feature request here.
```

With templates in place, initiating a new issue will present you with the following options:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/c4809025-ae82-424c-84bc-8e127569b99f)

## References

* [**Issues**](https://docs.github.com/en/issues)
* [**Attaching files**](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/attaching-files)
* [**Configure issue templates for your repository**](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository)
* [**Labels and Milestones**](https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work)

[**Home**](./readme.md) | [**Previous**](./repositories.md) | [**Next**](./projects.md)