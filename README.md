# cesium-workshop

<p align="center">
    <a href="http://cesiumjs.org/">
        <img src="https://github.com/AnalyticalGraphicsInc/cesium/wiki/logos/Cesium_Logo_Color.jpg" width="50%" />
    </a>
</p>

A simple JavaScript app showcasing some features of [Cesium](http://cesium.agi.com/), the open-source WebGL virtual globe and map engine.  Just fork this repo and start coding.

**Cesium version**: [1.34](http://cesiumjs.org/downloads.html).

**License**: Apache 2.0.  Free for commercial and non-commercial use.  See [LICENSE.md](LICENSE.md).

This application is intended to introduce the main features of Cesium in context, but it is by no means exahustive. Feel free to fork and modify this example however you'd like.

Local server
------------

A local HTTP server is required to run the app.

Have python installed?  If so, from the `cesium-workshop` root directory run
```
python -m SimpleHTTPServer
```
(Starting with Python 3, use `python -m http.server 8000`).

Browse to `http://localhost:8000/`

No python?  Use Cesium's node.js server.

* Install [node.js](http://nodejs.org/)
* From the `cesium-workshop` root directory, run
* `npm install`
* `node server.js`

Browse to `http://localhost:8000/`

What's here?
------------

* [index.html](index.html) - A simple HTML page. Run a local web server, and browse to index.html to run your app, which will show our sample application.
* [Source](Source/) - Contains [App.js](Source/App.js) which is referenced from index.html.  This is where the app's code goes.
* [ThirdParty](ThirdParty/) - A directory for third-party libraries, which here includes just Cesium.  See the **Updating Cesium** section for how to use the latest version from the Cesium repo.
* [server.js](server.js) - A simple node.js server for serving your Cesium app.  See the **Local server** section.
* [package.json](package.json) - Dependencies for the node.js server.
* [LICENSE](LICENSE) - A license file already referencing Cesium as a third-party.  This starter app is licensed with [Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0.html) (free for commercial and non-commercial use).  You can, of course, license your code however you want.
* [.gitignore](.gitignore) - A small list of files not to include in the git repo.  Add to this as needed.

Hosting your app on GitHub Pages
--------------------------------

If your app only requires static file serving (i.e. no proxying etc) it can be hosted using [GitHub Pages](https://pages.github.com/).
* Push your app to a gh-pages branch on github.  If you want to push from master you can use this command:
`git push origin master:gh-pages`
* After about 10 mins or so you can view your app with a URL like [http:/**my-github-username**.github.io/**my-awesome-cesium-app**/](http://my-github-username.github.io/my-awesome-cesium-app/)

Updating Cesium
---------------

The built Cesium source is in [ThirdParty/Cesium/](ThirdParty/Cesium/).  I sync this up with the master branch in the [Cesium repo](https://github.com/AnalyticalGraphicsInc/cesium) once in a while.  With `cesium` and `cesium-starter-app` repo directories in the same parent directory, here's up to update (replace `b25` with the tag/commit to update to):
```
cd cesium
git pull
git checkout -b 1.0-starter 1.0

./Tools/apache-ant-1.8.2/bin/ant clean combine
rm -rf ../cesium-workshop/ThirdParty/Cesium/*
cp -R Build/Cesium/* ../cesium-workshop/ThirdParty/Cesium/
git checkout master
git branch -d 1.0-starter
```
Then update the version in [package.json](package.json) and at the top of this README.md.

Test the starter app in case any changes are needed to [index.html](index.html) or [App.js](Source/App.js).

This uses the unminified version of Cesium.js, which is great for debugging but is quite large for production deployments.  To use the minified version, run `ant` with `minify` instead of `combine` before updating `cesium-starter-app`:
```
./Tools/apache-ant-1.8.2/bin/ant clean minify
```
The [Cesium Contributor's Guide](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Contributor's-Guide) has more info on Cesium build options.

Cesium resources
----------------

* [Forum](http://cesium.agi.com/forum.html)
* [Tutorials](http://cesium.agi.com/tutorials.html)
* [Sandcastle](http://cesium.agi.com/Cesium/Apps/Sandcastle/index.html) - lots of examples to copy and paste.
* [Reference Documentation](http://cesium.agi.com/refdoc.html)
