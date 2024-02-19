# cs-3250-actions-demo
## Step-by-step guide to cloning a repo, installing & running pytest, and setting up GitHub Actions for automated unit testing, linting, and formatting

### Clone the repo

First, make sure you are signed in to GitHub. Fork this repo by visiting https://github.com/bednie/cs-3250-actions-demo/fork. Create a fork with yourself as the owner. 

Next, in VS Code, open a new window, and click "Clone Git Repository...".

At the top of the window, paste in your repo's .git link, https://github.com/{your_username}/cs-3250-actions-demo.git, and hit enter. 

Then select the local folder where you would like this repo to be located. It is a good idea to put it in its own temp folder so it can be deleted easily once you finish this demo.

Now you can open the repo and begin the next section of this demo. 

### Automating unit tests & other actions

We can automate unit tests, and even other actions like linting and formatting.

GitHub Actions is one way to do this. Actions has many templates, or you can set up an action with your own YAML script, the configuration file format that Actions uses.

For this demo, you can download these two files by clicking the links and doing "Save as..." pytest.yml and ruff.yml,respectively: 

- [pytest.yml](https://gist.githubusercontent.com/bednie/bbf1418b5a5af15cfb0a548a4865cfec/raw/d68b6f0568532209ec35056cf01e9058955a92e8/pytest.yml)

- [ruff.yml](https://gist.githubusercontent.com/bednie/7d2863227e4263b618eb91656681227d/raw/d1f1017a7dd73803de09198dc43855493b729ac5/ruff.yml)

Now that you have downloaded these files, we will need to put them in a special folder so that GitHub Actions knows where to find them. 

In the root of this demo repo, you will see a directory called ".github" (the "." is important so make sure to include it in your own repos. Also, this folder will be hidden--make sure to set hidden folders to be visible on your machine), and then within .github/, you will see another directory called "workflows".

Placing your YAML scripts in ./github/workflows/ allows Actions to discover and run them automatically. You will see pytest.yml and ruff.yml in ./github/workflows/, which you can use as a starting point for your own Actions. 

### Running GitHub Actions

In order for the Actions to run, we need to set the repos permissions. Go to https://github.com/{your_username}/cs-3250-actions-demo/settings/actions and update the Workflow Permissions at the bottom of the page to allow "Read and write permissions" as well as "Allow GitHub Actions to create and approve pull requests". See the screenshot below:

![workflow-permissions.png](/workflow_permissions.png)

Now, when we push changes to the repo, the Actions will run. 

To make sure the Actions are actually doing something, let's add a failing test. In ```test_demo_functions.py```, you will see a commented-out unit test. Remove the #s to activate this test, and then push the changes to your remote GitHub repo:

```
def test_false():
    assert False, "This will always fail"
```

### Checking results of Actions runs 

When we attempt to push this code to our remote repo on GitHub, Actions will run the ruff linter & formatter as well as the unit tests.

We can view past runs' results and re-run jobs here: https://github.com/{your_username}/cs-3250-actions-demo/actions

A failed pytest run should be visible here if you merged in the failing test above.

### Next steps 

This is just a demo: it is possible to add more Actions, and even disallow merges with failing tests, by editing the .yml files in ".github/workflows/".

Add a workflow status [badge](https://docs.github.com/en/actions/monitoring-and-troubleshooting-workflows/adding-a-workflow-status-badge).

Check out the [Actions documentation](https://docs.github.com/en/actions). 
