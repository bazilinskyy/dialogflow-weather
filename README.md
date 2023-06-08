# DialogFlow chatbot with the use of World Weather API
## Instructions
1. Create a [Dialogflow agent](https://console.dialogflow.com).
2. Clone repository with `git clone https://github.com/bazilinskyy/dialogflow-weather.git` (or download the zip file and unarchive).
3. In Dialogflow console under **Settings** ⚙ > [Restore from Zip](https://dialogflow.com/docs/agents#export_and_import) using the `weather-bot.zip` in this directory.
4. Get a WorldwWatherOnline (WWO) API key from the [WWO website](https://developer.worldweatheronline.com/api).
    + You can register for a 30 days trial for trying things out.
5. Replace **<ENTER_WWO_API_KEY_HERE>** with your WorldwWatherOnline API key on the line under the comment `// API key from World Weather API` in `functions/index.js`. The resulting line should be like `const wwoApiKey = 'jfsdnf5irer343rnfis242enf23wew232njk23n4k2';`.
6. `cd` to the `functions` subdirectory of the directory of the repository.
7. Run `npm install`.
6. `cd ..` to get back to the root folder.
8. Install the Firebase CLI with `npm install -g firebase-tools`.
9. Login to your Google account with `firebase login`.
10. Initialise the Firebase project with `firebase init functions`.
      + Select **Add Firebase to an existing Google Cloud Platform project**. In Dialogflow console under **Settings** ⚙ > **General** tab > see the **Project ID** to be used.
      + **What language would you like to use to write Cloud Functions?** JavaScript
      + **Do you want to use ESLint to catch probable bugs and enforce style?** No
      + **File functions/package.json already exists. Overwrite?** No
      + **File functions/index.js already exists. Overwrite?** No
      + **Do you want to install dependencies with npm now?** No (we already did in step 7).
11. Run `firebase deploy --only functions`.
      + You will be asked to upgrade to the paid version of Firebase. Do it.
12. When successfully deployed, copy the Function URL from the resulting message in the console.
      + For example: `Function URL (dialogflowFirebaseFulfillment(us-central1)): https://us-central1-<PROJECTID>.cloudfunctions.net/<FUNCTIONNAME>`
13. Back in Dialogflow Console > **Fulfillment** > **Enable** Webhook.
14. Paste the the Function URL into the **URL** field > **Save**.

## Logging
Realtime logs can be monitored in the terminal with a command `npx firebase-logging --project=<PROJECTID> --freq=1500` which refreshes the log every 1.5 s in this case.

## Troubleshooting
### Firebase is not able to deploy
#### Possible cause 1
You ran the `firebase init functions` command not from the root folder but from the **/functions** subfolder. Indication of that is the newly created **/functions** folder inside of the **/functions** subfolder (**/functions/functions**).

## Inspiration
Based on [fulfillment-weather-nodejs](https://github.com/dialogflow/fulfillment-weather-nodejs).
