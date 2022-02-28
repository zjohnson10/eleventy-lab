### [Return to posts page](/eleventy-lab/posts)


# Basic Web Components with Open-wc, npm, node.js, and VScode

In order to start talking about web components and using open-wc, we have to introduce the building blocks that allow us to make that possible. To use open-wc, we have to install a few different dependencies that make it function. Before we install, let's talk about a few of them. First is npm, which is a JavaScript Node package manager. It offers the largest selection of code packages in their software registry. This is typically concurrently used with Node.js. Node.js is a open-source JavaScript runtime environment where code can be executed outside of the web. 

Both of these JavaScript add-ins make developers lives much easier. They are free to use and open-source that make it possible to share software with others and do things that were not possible before their development. They are very commonly used in web development with back-end tools to allow for runtime processes that can occur quicker and more efficient in the web. Now, let's look at installing these JavaScript helpers.

### Node.js
Go to this [webpage](https://nodejs.org/en/download/) and download the LTS version of nodejs for your device. Open the package in your downloads file folder and follow the directions to install.

### npm
For npm, this can be done in the command line / terminal. Directions can be found [here](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) to download and install. After running that command, the commands `node -v` and `npm -v` can be used to check that the most current version is installed.

### Yarn
Another software component we use for web develop is Yarn. We can install this in the command line with npm with the command `npm install --global yarn`. To check the version, use command `yarn --version`.

### Visual Studio Code
VSCode can be downloaded and installed [here](https://code.visualstudio.com/docs/setup/mac). VSCode is a coding text editor for many different programming languages.

## Build a Web Component
Now that we have installed those dependencies, we can make a web component with open-wc. Create a new folder/directory to house this project using either your file explorer or in the terminal with command `mkdir`. In your terminal, run the command `npm init @open-wc`. If this command was successful, you have installed everything correctly and you should see this! 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/eu69dor055gc7f6kebir.png)

When setting up the web component, the parameters I used were:
* Scaffold a new project
* Web component
* Linting, Testing, and Demoing
* No typescript
* Install with npm

From this, open-wc should open a new tab in your web browser showing this:

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/p6w98iksdvbcfw4uj2g1.png)

Congratulations you have successfully made a web component/element!

The github repository containing the code for the web element is [here](https://github.com/zjohnson10/zjohnson-lab1.git).


