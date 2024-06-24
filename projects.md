# Projects

[**Home**](./readme.md) | [**Previous**](./issues.md) | [**Next**](./branches.md)

A project is an adaptable collection of items that you can view as a table, a kanban board, or a roadmap and that stays up-to-date with GitHub data. Your projects can track issues, pull requests, and ideas that you note down.

> For a deep dive on Projects, see the [**References**](#references) section below.

## Create a Project

To create a project, navigate to the **Projects** section of your organization or personal account:

**Organization Projects URL**
```
github.com/orgs/<org>/projects
```

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/f8879d58-ce76-44fb-8725-246203bcf2c3)

**Personal Projects URL**
```
github.com/<user>?tab=projects
```

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/f2ff8da5-5f13-4f28-a3f0-d9e241d33080)

Clicking the **New Project** button will open up a new project wizard that allows you to select pre-configured templates to initialize your project from. Alternatively, you can start with just a simple view and build out the project yourself.

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/269cc602-4f92-4c39-9b54-66c474436a87)

For the sake of this documentation, I'm just going to start with a simple **Table** project and give it the name *Documentation Project*:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/bfcaa3fa-b4db-4a6e-87ee-59784082b25d)

After clicking **Create Project**, the project is created with an empty table.

## Link Items to a Project

Currently, we have a project but it isn't actually linked to anything in GitHub. We can fix this by linking a repository to the project. This can be done by navigating to the **Projects** view for the repository:

**Repository Projects URL**  
```
github.com/<org-or-user>/<repo>/projects
```

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/a49c46b7-f904-47fc-bbb7-2173f8ca7b71)

Clicking **Link a project** will allow you to connect the repository to an existing project:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/ea6034ee-9c6f-4ea7-8622-68dff3d12088)

Selecting *Documentation Project* will allow the project to start tracking issues and pull requests generated within the repository.

To lead into the next section, I'm going to create two issues with different labels within the repository:

**Documentation Issue**

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/e75b3d75-f7b4-4803-8320-22256bd6dd78)

**Enhancement Issue**

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/715abcf3-41cf-4b41-bcbc-87e67d1541fe)

After both issues are created, you can see the project table is updated to reflect the new items being tracked:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/10abc106-7f1a-4268-9662-9dd9f8c0f5e7)

## Workflows

Projects includes built-in workflows that you can use to update the **Status** of items based on certain events. By default, our project will set the **Status** of issues and pull requests to *Done* when they are closed.

When we created the issues in the section above, they were added to the project but they were not assigned a status. The following steps will configure the **Item added to project** workflow and set the **Status** of newly added items to *Todo*.

From the project route, click the three-dots menu to the top right of the table and click **Workflows**:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/cb1999b8-a05b-4015-a52b-f38ef1650ca2)

Select the **Item added to project** workflow in the left sidebar and click **Edit**:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/66bf3225-27e2-4139-8b64-e18752a256ad)

By default, it is configured to set the status of **issue** and **pull request** items to *Todo* when added to the project. Click **Save and turn on workflow** to accept these defaults.

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/f18542a2-7b76-4016-b8fe-b9cedffba9e4)

By adding the following issue and clicking **Submit new issue**:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/57d1e1c3-b3ae-4732-948a-6acc11d1171d)

You can see that the **github-project-automation** bot will move the issue to the *Todo* status in the project:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/321ee778-9f61-4cd1-a51e-8b52aa39eba9)

Go ahead and set the rest of the project issue's status to *Todo* by modifying the value directly in the project table:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/123e28a2-aa18-4f87-b449-03d55ea5f93e)

## Organize With Views

Right now, the project only has three simple issues. Over time, the complexity of the project will turn the table into an unwieldy table that will be difficult to understand. Luckily, projects are not just limited to a single view, and there are some adjustments that can be made to the main table that will make it a lot easier to reason about as it grows.

If you click the menu button next to the view tab label, you will get a list of options for configuring the view:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/0b61079b-d66c-4e2f-ac84-3f9be8812e78)

I'm going to add the **Labels** and **Linked pull requests** fields to the table view:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/86ef8c99-0e9d-4a2f-9a39-74211e97d342)

Note that you can re-organize the order of the columns by simply dragging the columns to where you want them to be in the layout.

Additionally, I'm going to group the items by **Status**:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/0b83ab6c-f3f7-4e0e-a78b-e34fc137b648)

Currently, grouping by status may not seem to be very helpful as everything is currently in the *Todo* status, but as more items are added and worked on, it will be helpful to have the items properly sorted in the main view.

To persist the changes, you simply need to click **Save**. The final change I will make will be to rename the table view to *Table - All*. This can be done simply by clicking the view tab label and changing the value:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/c119be8a-98d2-4186-82cf-7b14d385123f)

### Filtered Views

Leveraging view filters, views can be created that isolate related items together. For instance, you can create a view that only contains items with the *documentation* label. Or you can create a view for all items assigned to a particular user.

To do so, start by clicking the **+ New view** button to the right of the *Table - All* tab. This time, create a **Board** layout.

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/df84ee04-eee5-418f-964a-bd53b989a9fe)

Using the *Filter by keyword or by field* input below the tabs, you can customize which items appear in the view based on the item metadata. You can combine filters and save them as views.

In the example that follows:

* The filter is set to `label:documentation` indicating that only items with the label *documentation* will be rendered in this view.
* The name of the view has been updated to *Documentation*.
* The included fields were updated to include: label, pull request, and milestone.
* The changes were saved with the **Save** button.

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/a8eaae0f-bd14-4d10-ae83-83189ba362ef)

The tables below provide a basic guide to setting filters. For a more comprehensive guide to filtering, see [**Filtering projects**](https://docs.github.com/en/issues/planning-and-tracking-with-projects/customizing-views-in-your-project/filtering-projects).

**Filtering for fields**

Qualifier | Example
----------|--------
`assignee:USERNAME` | **assignee:octocat** will show items assigned to @octocat.
`label:LABEL` | **label:bug** will show items with the "bug" label applied.
`field:VALUE` | **status:done** will show items with the "status" field set to "done".
`reviewers:USERNAME` | **reviewers:octocat** will show items that have been reviewed by @octocat.
`milestone:MILESTONE` | **milestone:"Beta release" will show items assigned to the "Beta release" milestone.

**Combining filters**

You can create filters for multiple fields. Your view will show items that match all filters.

Qualifier | Example
----------|--------
`assignee:USERNAME field:VALUE` | **assignee:octocat priority:1** will show items assigned to @octocat that have a priority of 1.

You can also filter for multiple values from the same field. If you separate the values with commas, your view will show items that match any of the provided values.

Qualifier | Example
----------|--------
`assignee:USERNAME,USERNAME` | **assignee:octocat,stevecat** will show items assigned to either @octocat or @stevecat.

To filter for multiple values from the same field but show items that match all of the provided values, you can repeat the qualifier for each value.

Qualifier | Example
----------|--------
`assignee:USERNAME assignee:USERNAME` | **assignee:octocat assignee:stevecat** will show items that are assigned to both @octocat and @stevecat.

You can also combine filters that match some and match all items.

Qualifier | Example
----------|--------
`field:VALUE,VALUE assignee:USER assignee:USER` | **label:bug,onboarding assignee:octocate assignee:stevecat** will show items that have either the bug or onboarding labels but are assigned to both @octocat and @stevecat.

**Negating a filter**

You can invert any filter, including combinations, by prefixing with a hyphen.

Qualifier | Example
----------|--------
`-assignee:USERNAME` | **-assignee:octocat** will not show any items assigned to @octocat.
`-field:VALUE` | **-status:done** will not show any items with a status of "done".
`-field:VALUE,VALUE` | **-priority:1,2** will not show any items with a priority of either 1 or 2.

**Filtering for items that are missing a value**

You can use `no:` to filter for items that are missing a value.

Qualifier | Example
----------|--------
`no:assignee` | **no:assignee** will show any unassigned items.
`no:reviewers` | **no:reviewers** will show pull requests that do not have a reviewer.
`no:FIELD` | **no:priority** will show items with an empty priority field.

## Project Flow

Items added to a project are automatically updated as their work is conducted through GitHub. To demonstrate, I will conduct a pull request that closes the issue **A Documentation Issue**.

Because this pull request is directly associated with a project issue, I will not directly tag with labels or add to the project. I'll simply link it to the associated issue with a [**closing keyword**](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/using-keywords-in-issues-and-pull-requests).

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/24b8ed02-244c-4ecb-84f9-eb70c87cc0ee)

After merging the pull request:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/10bac12d-5c9d-4a85-8f5d-b812b55d0c9e)

The issue is automatically updated with a **Status** of *Done*:

![image](https://github.com/JaimeStill/JaimeStill/assets/14102723/864b8b18-bf67-4e48-aaab-3c724ac19143)

Notice how now that there are items with different statuses, the project table is able to group items into their appropriate status groups.

## References

* [**Planning and Tracking with Projects**](https://docs.github.com/en/issues/planning-and-tracking-with-projects)
* [**Filtering projects**](https://docs.github.com/en/issues/planning-and-tracking-with-projects/customizing-views-in-your-project/filtering-projects)
* [**Using keywords in issues and pull requests**](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/using-keywords-in-issues-and-pull-requests)

[**Home**](./readme.md) | [**Previous**](./issues.md) | [**Next**](./branches.md)