# Azure webapp slot deployment

This is a demo to show how we can deploy to Azure webapp slot with
GitHub action.

## Steps to run the sample

- Create a new ASP.NET MVC application
- Open Azure Portal and create a new webapp with name `webapp-0707`
- Create a slot with name `test` in the webapp
- Create a GitHub workflow to deploy in the slot with `azure/webapps-deploy@v2`
```
- name: 'Deploy to Azure WebApp'
  uses: azure/webapps-deploy@v2
  with:
    app-name: webapp-0707
    slot-name: test
    publish-profile: ${{ secrets.AZURE_WEBAPP_PUBLISH_PROFILE_TEST }}
    package: ./myapp
```
- Download the slot publish profile and save in the GitHub secret
- Push the MVC Application to GitHub

In every push to the `main` GitHub action will deploy to the `test` slot. After that
we can check the application manually with the slot URL and if everything is good then 
swap slot from Azure Portal.

Note: Because this is a demo for security reasons publish profile has been removed from 
the GitHub secret.
