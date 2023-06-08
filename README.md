# DialogFlow chatbot with the use of World Weather API
## Instructions
1. Create a [Dialogflow agent](https://console.dialogflow.com).
2. `git clone https://github.com/bazilinskyy/dialogflow-weather.git`.
3. In Dialogflow console under **Settings** ⚙ > [Restore from Zip](https://dialogflow.com/docs/agents#export_and_import) using the `weather-bot.zip` in this directory.
4. Get a WorldwWatherOnline (WWO) API key from https://developer.worldweatheronline.com/api.
    + You can register for a 30 days trial for trying things out.
5. Replace **<ENTER_WWO_API_KEY_HERE>** with your WorldwWatherOnline API key on the line under the comment `// API key from World Weather API` in `functions/index.js`
6. `cd` to the `functions` subdirectory of the directory of the repository.
7. Run `npm install`.
8. Install the Firebase CLI with `npm install -g firebase-tools`.
9. Login to your Google account with `firebase login`.
10. Initialise the Firebase project with `firebase init functions`.
      + Select **Add Firebase to an existing Google Cloud Platform project**. In Dialogflow console under **Settings** ⚙ > **General** tab > see the **Project ID** to be used.
      + You can overwrite the existing codebase and choose not to overwrite the **index.js** and **packages.json** files.
11. Run `firebase deploy --only functions`.
12. When successfully deployed, visit the **Project Console** link > **Functions** > **Dashboard**.
      + Copy the link under the events column.
      + For example: `https://us-central1-<PROJECTID>.cloudfunctions.net/<FUNCTIONNAME>`.
13. Back in Dialogflow Console > **Fulfillment** > **Enable** Webhook.
14. Paste the URL from the Firebase console’s trigger column into the **URL** field > **Save**.

## Logging
Realtime logs can be monitored in the terminal with a command `npx firebase-logging --project=<PROJECTID> --freq=1500` which refreshes the log every 1.5 s in this case.

## Inspiration
Based on [fulfillment-weather-nodejs](https://github.com/dialogflow/fulfillment-weather-nodejs).