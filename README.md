# **Upptime: Monitor websites uptime with GitHub**

Here's what you get with Upptime:

- Monitor any website (yours or someone else's website) every 5 minutes with GitHub Actions. It also stores response time stats.
- You can configure downtime notification to be sent via email, Slack, Telegram and custom webhooks. This way you can easily find out when a website goes down.
- Optionally, you can set up a status page and share the URL with your team members or clients so that they can also visualize the uptime stats and outage history.
- If a server returns some response code other than 200, an issue will be generated automatically in the repository along with that being noticeable on the static frontend.

![Screen Shot 2021-02-01 at 7.18.19 PM.png]({{site.baseurl}}/Screen Shot 2021-02-01 at 7.18.19 PM.png)

## **Configuring Upptime for downtime monitoring**

- **Step 1. Create an identical Upptime repository**

It means having the same files and directory structure. You might think that you now have to fork the official repository, but that's not it. Upptime's official repository is a template repository.

A template repository is a special type of repository, which lets others create a similar 	repository from it (same files, same directory structure). One of the key differences between a template repository and a fork is that when you fork some repo, all the previous commits are now part of this forked repository, it's good for contributing to some project. On the other hand a template repository lets someone start a fresh new project with the same files and directories.

- Head over to Upptime's GitHub [repository](https://github.com/upptime/upptime). On the top right side you should be able to see a green button titled "Use this template". Click on it.

![Screen Shot 2021-02-01 at 7.31.46 PM.png]({{site.baseurl}}/Screen Shot 2021-02-01 at 7.31.46 PM.png)


- Now give this new repository a nice name. I'm going to name mine upptime. There's a checkbox above "create repository from template", labeled "Include all branches", make sure you check that. Otherwise, you won't be able to use GitHub Pages for the static website showing stats.

![Screen Shot 2021-02-01 at 7.33.15 PM.png]({{site.baseurl}}/Screen Shot 2021-02-01 at 7.33.15 PM.png)


- **Step 2. Configuration**

- Add GH_PAT

By default, Upptime checks if the given websites are up or not every five minutes, depending on the result it either opens an issue (in case a site is down) or commits the relevant information like status, response time, etc.

To do so, it needs access to this repository. So, you are going to provide it the access by providing it a personal access token.

Go to your account settings:

![Screen Shot 2021-02-01 at 7.34.31 PM.png]({{site.baseurl}}/Screen Shot 2021-02-01 at 7.34.31 PM.png)


- And click on "Developer settings" from the left sidebar. then select "Personal access tokens", and then hit the "Generate new token" option.

![Screen Shot 2021-02-01 at 7.37.09 PM.png]({{site.baseurl}}/Screen Shot 2021-02-01 at 7.37.09 PM.png)


- From this list, select "repo" and "workflow". Read the descriptions of these specific permissions to understand why we need to select these.


![Screen Shot 2021-02-01 at 7.37.54 PM.png]({{site.baseurl}}/Screen Shot 2021-02-01 at 7.37.54 PM.png)


- Give this token a name and finally click on "Generate token". Once you're able to see the key, copy it. Remember, you won't be able to see this again, either save it in a safe place or create a new one if needed later.

![Screen Shot 2021-02-01 at 7.38.32 PM.png]({{site.baseurl}}/Screen Shot 2021-02-01 at 7.38.32 PM.png)


- Next you need to add this token as a repository secret.

**"GitHub secrets are encrypted environment variables available to various GitHub action workflows. In easier terms these environment variables are available to the processes being run under GitHub actions."**

- Go to your version of the Upptime repository's settings and select "secrets" on the left sidebar and then click the "New repository secret" button then, Here for the name, enter GH_PAT and in the value field, paste the token. Finally, click on the "Add secret" button.

- You should see a screen like this at the end:

![Screen Shot 2021-02-01 at 7.42.17 PM.png]({{site.baseurl}}/Screen Shot 2021-02-01 at 7.42.17 PM.png)


**Update .upptimerc.yml**

- Change the value of owner to your GitHub username.
- Change the value of repo to your repository name. The above options are necessary for Upptime to be able to push commits and open issues.
- If you have a custom domain, add that to the cname variable. If not, like me, remove the line altogether.
- If you did not have a custom domain, uncomment the baseUrl line, and change the value to your GitHub repository name.
- Change the sites array according to your needs. I have set Linux_Shell_Script to monitor.

![Screen Shot 2021-02-01 at 7.43.15 PM.png]({{site.baseurl}}/Screen Shot 2021-02-01 at 7.43.15 PM.png)

- Save the file and push to master/main.

- **Step 3. Publish the page**

If you want to have a status showing frontend, this section is for you.

Head over to your repository settings. On the Options list of configurable options, find the section that's titled GitHub Pages.

From the branch dropdown menu, select the branch named gh-pages and choose root for web root directory. Click Save.

![Screen Shot 2021-02-01 at 7.45.29 PM.png]({{site.baseurl}}/Screen Shot 2021-02-01 at 7.45.29 PM.png)


Finally, wait a few moments for the actions to complete. You can check the progress in the Actions menu found on the repository page.

Once all actions are completed check the link of uptime repository for dashboard.

![Screen Shot 2021-02-01 at 7.47.48 PM.png]({{site.baseurl}}/Screen Shot 2021-02-01 at 7.47.48 PM.png)


















