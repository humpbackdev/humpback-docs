# Profiling your project with Blackfire.

When we are working on a project and this project start experiencing performance issues we often need to do some profiling procedure to try to find the problem that is affecting our project. The configuration of profiling tools frequently consume us a lot of time so, what if we can improve that setup time and even have understandable profiling results? that's what we did when Blackfire was included to this project.

Blackfire is profiling tool that allows us to profile in really easy way, if you want to know more about blackfire you could would visit this page [Blackfire documentation](https://blackfire.io/docs/introduction).

## Configuring our blackfire.

- First at all we need you to create new blackfire account.
- Then we need you to go your settings page and find the Credentials page (https://blackfire.io/my/settings/credentials)
- Once on the credentials page as you can see there are some keys for different proposes, in this case we **only need the server related keys**, specifically the **Server ID and the Server Token**
- Copy the server id and the server token and assign those values to environment variables `BLACKFIRE_SERVER_ID` and `BLACKFIRE_SERVER_TOKEN` into the `.env` file in the root path your project.
- Now install the Companion browser plugin, if you use google chrome use the following guide: [Chrome Companion guide](https://blackfire.io/docs/integrations/chrome#installing-the-companion) and if you use Firefox use the following guide: [Firefox Companion guide](https://blackfire.io/docs/integrations/firefox#installing-the-companion)
- Once the browser plugin is installed you should be able to execute the profiling process over any page of your project just pressing the Blackfire profile button in tool bar of your browser.


Enjoy your profiling!!!.
