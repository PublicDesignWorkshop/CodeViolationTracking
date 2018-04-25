# Code Violation Tracking

Code Violation Tracking is a React/NodeJS/Express web application for submitting and processing housing code violations.

This app allows users to download our [code violation form](https://github.com/PublicDesignWorkshop/CodeViolationTracking/blob/master/client/public/static/BbB_Form.pdf), which they can use to take note of a housing code violation. Then, users can transcribe the form to a matching web form on our app, which when submitted will process and enter the new code violation data to Google Sheets.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

You'll need to install Node (v8.9.4) and NPM (v5.6.0)

### Installing

There are two embedded Node projects in this repo. The first is at the root level, and handles the server. The second's root is the client folder, and houses the React app.

First, install all dependencies in both the root

```
npm install
```

And the client

```
cd client
npm install
```

Next, you'll need to create a .env file in the root folder to set up the development environment

```
cd ..
touch .env
nano .env
```

The .env file contains the environment variables, which can be different for different developers and the deployed environment.

```
PORT=3000
PASSWORD='ChangeMe'
DRIVE_PHOTOFOLDERID='1SZCKBKIBuApDf-BlDQ3maeYZUvjWh1ZUpVBr6BPL9PY'
DRIVE_SPREADSHEETID='1EQ2bl80mbuFpf-1j-9NTS5AvGvN7GwBjtpECrT3FN94'
```

PORT is the port used by the Express server to serve the app. In a development env it can't be 3000 because that's what react uses

PASSWORD is the password used to control access to the web form. There is no user system, instead a single password can be shared between any number of volunteers

DRIVE_PHOTOFOLDERID is the id of the root folder on Drive where photos will be stored

https://drive.google.com/drive/folders/HeresWhereIDIsInURL

DRIVE_SPREADSHEETID is the id of the spreadsheet that data will be stored on.

https://docs.google.com/spreadsheets/d/HeresWhereIDIsInURL/editOnce 

Next, you need to upload the Template_Spreadsheet.xlsx file in this repo to the Google Drive account you're planning on using. You'll also need to create a new folder for photos to be uploaded too. Once you have both, copy and paste their IDs into your .env file.

Next, you need to create and download Google API keys for your instance of this project. Those can be downloaded at https://console.developers.google.com

You'll need to 

1. Create a new project
2. Navigate to "Dashboard"
   1. Enable the Google Drive API
   2. Enable the Google Sheets API
3. Navigate to "Credentials" 
   1. Select "Create Credentials"
   2. Select "Service Account Key"
4. Select or Create a new Service account
   1. Give it a name and set it's role to "Account" "Owner"
   2. Make a note of it's service account ID
   3. Set it's key type to JSON
5. You'll then automatically download a JSON file with your new credentials on it. Place it in your root folder, name it "master-creds.json" and add it to your .gitignore!

Last, you need to give access to the photo folder and spreadsheet to this new service account. The easiest way to do this is to place both the spreadsheet and photo folder inside of another folder, and give the service account write access to the folder and it's contents.

You can do this by right-clicking on a file or folder on Drive and using the "Share" option. Enter the service account ID (it'll look like a gmail address) in the invite section at the bottom and give the service account write access. 

Finally, you're done! Return to the root folder and try running the app using npm start.

```
npm start
```

npm start runs the server using nodemon (which restarts the server automatically) and the react app using concurrently. 

If both installed properly, a react app should start and open in your default browser and a server should pop up in your log

## Deployment

Deployment should be relatively painless, compared to setup. We're architected the repo in such a way that you should only need to 

1. Clone this repo onto your web server
2. Ensure that the .env file has been created and matches your development one (with an updated port)
3. Upload your master-creds.json file
4. Install dependencies
5. Run npm run build in the client folder

```
cd client
npm run build
```

Once a build is complete, and you've configured your web server to support your chosen port and the build folder, simply start node using the server.js file!

## Built With

* [React](https://reactjs.org/)
* [Node](https://nodejs.org/en/)
* [Express](https://expressjs.com/)
* [Google API NodeJS Client](https://github.com/google/google-api-nodejs-client)

## Contributing

At this time we are not accepting contributors

## Known Issues

- **When a new address is used or created, if a user selects more than one code violation the system will push each into a duplicate folder on drive.**
  We're not sure what the cause is, but it's related to the way Upload() and the data submission path work together.

## Authors

* **[Pierce McBride](https://github.com/McBrideMusings)** - Design and Development
* **[Brendan Cecere](https://github.com/bcecere3)** - Design and Development
* **[Rachel Chen](https://github.com/rachelwchen)** - Design
* **[Morgan Orangi](http://morganorangi.com/)** - Design

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* [Digital Media Program](http://dm.lmc.gatech.edu/) at Georgia Institute of Technology
* [Carl DiSalvo](https://www.iac.gatech.edu/people/faculty/disalvo), our professor on the project and the head of the RED ATL Lab


