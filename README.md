# cs-3250-actions-demo
## Step-by-step guide to cloning a repo, installing & running pytest, and setting up GitHub Actions for automated unit testing, linting, and formatting

### Clone the repo

First, make sure you are signed in to GitHub. Fork this repo by visiting https://github.com/bednie/cs-3250-actions-demo/fork. Create a fork with yourself as the owner. 

Next, in VS Code, open a new window, and click "Clone Git Repository...".

At the top of the window, paste in your repo's .git link, https://github.com/{your_username}/cs-3250-actions-demo.git, and hit enter. 

Then select the local folder where you would like this repo to be located. It is a good idea to put it in its own temp folder so it can be deleted easily once you finish this demo.

Now you can open the repo and begin the next section of this demo. 

### Automating unit tests & other actions

We can automate unit tests, and even other actions like linting and formatting. This is very helpful if we forget to run tests after making changes, or if we have a repo open to contributions from many people, or if we want to automate building, testing, and deploying our software, or--you get the idea. GitHub Actions is one way to do this. Actions has many pre-made templates, or you can set up an action with your own YAML configuration file (.yml).

For this demo, we will be using two YAML config files--one for unit tests (using pytest), and one for linting and formatting (using ruff). You may downloaded these files (right click and "Save as..." pytest.yml and ruff.yml,respectively), and use them as a starting point for your own Actions: 

- [pytest.yml](https://gist.githubusercontent.com/bednie/bbf1418b5a5af15cfb0a548a4865cfec/raw/d68b6f0568532209ec35056cf01e9058955a92e8/pytest.yml)

- [ruff.yml](https://gist.githubusercontent.com/bednie/7d2863227e4263b618eb91656681227d/raw/d1f1017a7dd73803de09198dc43855493b729ac5/ruff.yml)
  
These YAML files are also present in this repo. In the root of this demo repo, you will see a directory called ".github" (the "." is important so make sure to include it in your own repos. This folder will be hidden by default--make sure to set hidden folders to be visible on your machine), and then within .github/, you will see another directory called "workflows".

Placing your YAML configs in ./github/workflows/ allows Actions to discover and run them automatically. 

### Running GitHub Actions

In order for the Actions to run, we need to set the repos permissions. Go to https://github.com/{your_username}/cs-3250-actions-demo/settings/actions and update the Workflow Permissions at the bottom of the page to allow "Read and write permissions" as well as "Allow GitHub Actions to create and approve pull requests". See the screenshot below:

![workflow-permissions.png](/workflow_permissions.png)

Now, when we push changes to the repo, the Actions will run. 

To make sure the Actions are actually doing something, let's add a failing test. In ```test_demo_functions.py```, you will see a commented-out unit test. Remove the #s to activate this test, and then push the changes to your remote GitHub repo:

```
def test_false():
    assert False, "This will always fail"
```

### Viewing results of Actions runs 

When we attempt to push this code to our remote repo on GitHub, Actions will run the ruff linter & formatter as well as the unit tests.

We can view past runs' results and re-run jobs here: https://github.com/{your_username}/cs-3250-actions-demo/actions

A failed pytest run should be visible here if you merged in the failing test above. 

### Next steps 

This is just a demo: try adding more Actions to automate the testing, building, and deployment of your work. 

Add a workflow status [badge](https://docs.github.com/en/actions/monitoring-and-troubleshooting-workflows/adding-a-workflow-status-badge).

Check out the [Actions documentation](https://docs.github.com/en/actions). 
