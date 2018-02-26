### Appveyor Notifications <br>

You can automate Appveyor notify you when a new build is generated by 2 ways: Your project settings and [appveyor.yml](https://www.appveyor.com/docs/notifications/)
Here I will show you the first one.

---

#### Appveyor Notifications by Project Settings <br>

1. Go to YourProject->Settings->Notifications.
2. Add a new notification.

You can set a lot of ways to be notified by. I specially like **Email Notifications** and **Slack Notifications** (specially if I'm working in a team on the same project).

  #### Email Notifications
  
  1. Select Email Notifications.
  2. Recipients: Introduce the email adresses where the notifications will be sent to, separated by commas.
  3. Subject: Choose the subject for the email. For example, failed build {{buildVersion}}
  4. Message: Customize your own message. For example, Build failed commited by {{commitAuthor}}({{commitAuthorEmail}})
  5. Events: Select the events you will be notified of. In this example we only want to be notified when a Build Failure happens.
  
  #### Slack Notifications
  
  1. Select Slack Notifications
  2. Go [HERE](https://api.slack.com/custom-integrations/legacy-tokens) and generate a token. If you are setting notifications by appveyor.yml be sure to encrypt this first going [HERE](https://ci.appveyor.com/tools/encrypt).
  3. Introduce your token in the Authentication Token Field.
  4. Choose the Slack channel where the notifications will be sent to.
  5. Configure your own message. You can customize it with variables like we did before.
  6. Select your events.
  