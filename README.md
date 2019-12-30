# forge-bim360.costmanagement.exchange.csv

[![Node.js](https://img.shields.io/badge/Node.js-8.0-blue.svg)](https://nodejs.org/)
[![npm](https://img.shields.io/badge/npm-4.0-blue.svg)](https://www.npmjs.com/)
![Platforms](https://img.shields.io/badge/Web-Windows%20%7C%20MacOS%20%7C%20Linux-lightgray.svg)
[![Data-Management](https://img.shields.io/badge/Data%20Management-v1-green.svg)](http://developer.autodesk.com/)

[![BIM-360](https://img.shields.io/badge/BIM%20360-v1-green.svg)](http://developer.autodesk.com/)
[![Cost Management](https://img.shields.io/badge/Cost%20Management-beta-green.svg)](http://developer.autodesk.com/)

[![MIT](https://img.shields.io/badge/License-MIT-blue.svg)](http://opensource.org/licenses/MIT)
[![Level](https://img.shields.io/badge/Level-Intermediate-blue.svg)](http://developer.autodesk.com/)


## Description
This sample demonstrates exchanging properties of Budget, Contract, Cost item and Change Order between cost module and .CSV file using BIM 360 Cost Management API. It includes 3 main tasks:
1. Display BIM 360 Cost properties either in **Raw data** and **Human reabable form**.
2. Export BIM 360 Cost properties either in **Raw data** and **Human reabable form** to a CSV file.
3. Import BIM 360 Cost properties from a locally stored CSV file(based on **Raw data**).

This sample is implemented based on Node.js version of [Learn Forge Tutorial](https://github.com/Autodesk-Forge/learn.forge.viewhubmodels/tree/nodejs), please refer to https://learnforge.autodesk.io/ for the details about the framework.

## Thumbnail
![thumbnail](/thumbnail.png)  

## Demonstration
Watch on [Youtube](https://youtu.be/5NeRK4H-ZrA) to learn more about using this sample to display and exchange BIM 360 cost information.


## Live Demo
[https://bim360cost-exchange.herokuapp.com/](https://bim360cost-exchange.herokuapp.com/)


# Setup
## Prerequisites
1. **BIM 360 Account**: must be Account Admin to add the app integration. [Learn about provisioning](https://forge.autodesk.com/blog/bim-360-docs-provisioning-forge-apps). 
2. **Forge Account**: Learn how to create a Forge Account, activate subscription and create an app at [this tutorial](http://learnforge.autodesk.io/#/account/). 
3. **Node.js**: basic knowledge with [**Node.js**](https://nodejs.org/en/).
4. **JavaScript** basic knowledge with **jQuery**

## Running locally
Clone this project or download it. It's recommended to install [GitHub desktop](https://desktop.github.com/). To clone it via command line, use the following (**Terminal** on MacOSX/Linux, **Git Shell** on Windows):

    git clone https://github.com/autodesk-forge/forge-bim360.costmanagement.exchange.csv

**Visual Sutdio Code** (Windows, MacOS):

Open the folder, at the bottom-right, select **Yes** and **Restore**. This restores the packages (e.g. Autodesk.Forge) and creates the launch.json file. 

At the `.vscode\launch.json`, find the env vars and add your Forge Client ID, Secret and callback URL. 

The end result should be as shown below:

```json
"env": { 
    "FORGE_CLIENT_ID": "your id here",
    "FORGE_CLIENT_SECRET": "your secret here",
    "FORGE_CALLBACK_URL": "http://localhost:3000/api/forge/callback/oauth"
},
```

To run it, install the required packages, set the enviroment variables with your client ID & secret and finally start it. Via command line, navigate to the folder where this repository was cloned and use the following:

    npm install 
    node start.js

Open the browser: [http://localhost:3000](http://localhost:3000). And follow the thumbnail.png to play the features.

## Deployment

To deploy this application to Heroku, the **Callback URL** for Forge must use your `.herokuapp.com` address. After clicking on the button below, at the Heroku Create New App page, set your Client ID, Secret and Callback URL for Forge.

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/JohnOnSoftware/forge-bim360.costmanagement.exchange.csv)




## Known issues
1. The 'scopeOfWork' property contain rich text which may includes '**\n**' and '**,**', but the 2 characters are reserved for special usage while parsing CSV file, to avoid the issue, I use the following 2 characters as replacement for 'scopeOfWork' property.
```js
        const Enter_Replacement = '\xfe';
        const Comma_Replacement = '\xfd';
```

## Tips & Tricks
1. Not all the properties could be updated, only these marked as **Editable** are supported.
2. To import properties from CSV file, the suggested way is to export a CSV file of **raw data** first, update the editable properties within the file, then import it back to BIM 360 cost module.

## Troubleshooting
1. **Cannot see my BIM 360 projects**: Make sure to provision the Forge App Client ID within the BIM 360 Account, [learn more here](https://forge.autodesk.com/blog/bim-360-docs-provisioning-forge-apps). This requires the Account Admin permission.
 

## Further Reading
- [BIM 360 API](https://developer.autodesk.com/en/docs/bim360/v1/overview/) and [App Provisioning](https://forge.autodesk.com/blog/bim-360-docs-provisioning-forge-apps)
- [Data Management API](https://developer.autodesk.com/en/docs/data/v2/overview/)

Tutorials:
- [View BIM 360 Models](http://learnforge.autodesk.io/#/tutorials/viewhubmodels)

Blogs:
- [Forge Blog](https://forge.autodesk.com/categories/bim-360-api)
- [Field of View](https://fieldofviewblog.wordpress.com/), a BIM focused blog

## License
This sample is licensed under the terms of the [MIT License](http://opensource.org/licenses/MIT). Please see the [LICENSE](LICENSE) file for full details.

## Written by
Zhong Wu [@johnonsoftware](https://twitter.com/johnonsoftware), [Forge Partner Development](http://forge.autodesk.com)
