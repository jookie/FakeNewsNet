# React Google News
![screenshot](readme_react_google_news.jpg)

### A simple [React](https://reactjs.org/) front end application using the [Google News API](https://newsapi.org/).
React Google News uses a lightweight Node Express back end to reroute API queries to a React front end. It displays trending articles in a responsive card grid format and allows the user to select from several popular news websites.

## Demo App
You can see a demo version of this application deployed to [Cyclic](https://app.cyclic.sh) here: https://react-google-news.cyclic.app

## Application Info
The project is configured with [Node Package Manager](https://www.npmjs.com/), [Webpack](https://webpack.js.org/), and [Babel](https://babeljs.io/).

It uses [webpack-merge](https://www.npmjs.com/package/webpack-merge) to separate development and production builds, but keep a common, reusable configuration. It is also configured for hot reloads in the Express server, so Webpack will rebuild when changes are made.

An Express back end is used to make API requests and protect the API key. Routes are configured for a select number of news websites to query articles from. All routes can be found in the [server.js](../master/server.js) file.

The application implements Bootstrap via [Reactstrap](https://reactstrap.github.io/). It makes front end API calls with [fetch](https://github.com/github/fetch).

## Commands
`npm run dev` - Build for development and run the Express server. Code changes will be implemented automatically through hot reloading.

`npm run build` - Use Webpack to build for production.

`npm run start` - Run the Express server via Node.

## Install Instructions
Node Package Manager (NPM) is used for dependencies. To install the application locally, follow these instructions:

1. Install [Node.js](https://nodejs.org/). NPM comes packaged with it.
2. Run `npm install` in the command line while in the project directory. It will install dependencies from the [package.json file](../master/package.json).
3. To build for development and run the local dev server at http://localhost:5000, run `npm run dev`. It will run the Node/Express application in the [server.js file](../master/server.js).

In order to access the News API, you must go to the API website and sign up for an account [here](https://newsapi.org/). Once you have an API key, configure it locally with [dotenv](https://www.npmjs.com/package/dotenv). Create a .env file and set `API_KEY="insert API key here"`. For production, set an environment variable manually through command line: `NODE_ENV=production, API_KEY=...`.


## Create your github repository
If you're receiving the "error: remote origin already exists" message while trying to set the remote origin and push the local branch to GitHub, it means that your repository already has an 'origin' remote set up.

This could happen if you've previously added an 'origin' remote or if the repository was cloned from GitHub, as 'origin' is the default name given to the remote repository when you clone.

To resolve this issue, you might want to ensure that you're inside the correct directory or repository where you want to perform these operations. Follow these steps:

1. Check your current remote configuration:
    ```bash
    git remote -v
    ```

2. If 'origin' is already set, you can proceed with updating the URL or pushing without adding 'origin':

    To update the URL of the existing 'origin':
    ```bash
    git remote set-url origin https://github.com/jookie/media.git
    ```

3. If you're in a new repository or the 'origin' remote is not configured properly, you can proceed with the following steps:

    Remove the existing 'origin':
    ```bash
    git remote remove origin
    ```

    Then add the 'origin' remote:
    ```bash
    git remote add origin https://github.com/jookie/media.git
    ```

4. Finally, set the branch and push to the 'main' branch:
    ```bash
    git branch -M main
    git push -u origin main
    ```

Ensure that you have the appropriate permissions to push to the repository on GitHub. If you're not the owner or don't have write access, you might encounter errors while pushing changes.

Be careful when manipulating remotes, as it can affect your Git setup. Always double-check the commands you're using and verify that they correspond to your intended actions.

## License
This project is open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

The error message "Error: listen EADDRINUSE: address already in use :::5000" typically indicates that the port number you're trying to use for your application is already in use by another process on your system.

Here are a few steps you can take to resolve this issue:

1. **Change the Port Number:** If you have control over the application's port number, you can modify it to use a different port that is not in use. For example, instead of port `5000`, you could try `3000`, `8080`, or any other available port.

2. **Identify and Terminate the Process:** You can identify the process that is using port `5000` and terminate it. On macOS, you can use the following command in the Terminal to find the process:

   ```bash
   lsof -i :5000
   ```

   This command will list the process using port `5000`. You'll get an output like:

   ```
   COMMAND  PID   USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
   node    1234   user   12u  IPv6 0x123456789abcdef      0t0  TCP *:5000 (LISTEN)
   ```

   Replace `1234` with the PID (Process ID) listed in your output and use the following command to terminate the process:

   ```bash
   kill -9 1234
   ```

   Replace `1234` with the PID of the process that is using port `5000`.

3. **Restart Your System:** If terminating the process doesn't work or if you're not sure which process is using the port, restarting your system can free up the port and resolve the issue.

4. **Check for Orphaned Processes:** Sometimes, even after stopping an application, the process might still be running in the background. Use `ps -ax | grep node` (if it's a Node.js process) or similar commands to check for such orphaned processes and terminate them.

Once you've freed up the port `5000` or switched to a different port for your application, try running your application again. If you're developing multiple applications, ensure that each one uses a unique port to avoid conflicts like this in the future.
