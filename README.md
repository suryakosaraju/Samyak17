#**An advanced Ionic v1.x template**

![Ionic Framework + Gulp](https://github.com/jdnichollsc/Ionic-Starter-Template/blob/gh-pages/images/ionic_40.png?raw=true)

#Introduction

You need to obfuscate your code and reduce the size of your mobile applications. With this project you can work with Gulp in the best way, allowing improve your development workflow. This project seeks to improve the following tasks:

- Design your application with a maintainable code using **Sass** and writing less code using **Autoprefixer**. Concatenate and Minify styles in a stylesheet.
- Concatenate and Uglify javascript files using Source maps to debug the code easily.
- Compress images to reduce the size of your application.
- Compress html templates, respecting your structure.
- Clean unnecessary files downloaded with Bower.
- Use CSS animations with **Animate.css**.
- Use **SQLite** with a service pattern. **You can use Pre-filled databases**.

# Demo

Do you want to see this starter in action? Visit https://jdnichollsc.github.io/Ionic-Starter-Template/ yay!
> Automatically deployed to GitHub Pages using Gulp - Check the **last task** into [gulpfile.js](https://github.com/jdnichollsc/Ionic-Starter-Template/blob/master/gulpfile.js)

<img width="242px" height="411px" src="https://s3.amazonaws.com/ionic-marketplace/ionic-starter-template/screenshot_1.png">
<img width="242px" height="411px" src="https://s3.amazonaws.com/ionic-marketplace/ionic-starter-template/screenshot_2.png">
<img width="242px" height="411px" src="https://s3.amazonaws.com/ionic-marketplace/ionic-starter-template/screenshot_3.png">

#Projects using this template
- **[Hartford Fashion Week](https://play.google.com/store/apps/details?id=fashion.hartford.app) - Created by [Matthew Seremet](http://matthewseremet.com/)**
- **[IonPhaser](http://market.ionic.io/plugins/ionphaser)**
- **[Ionic ElastiChat](https://jdnichollsc.github.io/Ionic-ElastiChat-with-Images/)**
- **[Ionic Drag and Drop](https://jdnichollsc.github.io/Ionic-Drag-and-Drop)**
- **[Game of Drones](https://github.com/jdnichollsc/Game-of-Drones)**

> Do you have a project using this template? Let me know to share it with everyone!

#Instructions

1. Download this template.
2. Execute the command `npm install`
3. Execute the command `gulp`
4. Run Ionic: 
   - `ionic serve` to test on the browser **(Gulp is running by default)**.
   - `ionic run android --livereload` to test on the device.
5. Modify this template and create your hybrid mobile app.
6. Check the **[John Papa's Angular Style Guide](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md)**.

#Template Structure

Path         | Explanation
----------   | -------------
`./app/img/` | Images in your app.
`./app/js/`  | Scripts (Controllers, Services, Directives, etc).
`./app/scss/` | The styles of your app using Sass.
`./app/templates/` | Views in your app. (Only html files)
`./app/index.html` | The init page.
`./www/css/` | Other css styles like **[Animate.css](https://daneden.github.io/animate.css/)**, etc.
`./www/lib` | Download scripts using bower.
 	 
#Using bower to download libraries (npm preen included)

* Download the script. Eg: `bower install ionic-datepicker --save`
* Add the path of the files that you will use in `bower.json` from `www/lib`. Eg:
```javascript
"preen": {
	//... More libraries
	"ionic-datepicker": [
		"dist/*.js"
		//Other files and folders will be deleted to reduce the size of your app
	]
}
```
* Run gulp in the CLI. Eg: `gulp` or `gulp lib`
* That's all, folks!!

#Animate elements using **[Animate.css](https://daneden.github.io/animate.css/)**

* Do you want to animate Modals? This template have an example. More examples **[here](https://github.com/kevincobain2000/ionic-animated-modal)**
```javascript
//Using the Modals service in this template
Modals.openModal($scope, 'templates/modals/users.html', 'animated rotateInDownLeft');
```
* Do you want to animate Popups and other elements? See an example:
```javascript
$ionicPopup.alert({
	title: 'Hello World',
	template: 'This is the best template to start with Ionic Framework!',
	cssClass: 'animated bounceInDown'
});
```

#SQLite databases on Android, iOS and Windows (Using **[cordova-sqlite-ext](https://github.com/litehelpers/cordova-sqlite-ext)** plugin)
This template include an example **(pre-populated database)**, you can test in the **browser** using **Google Chrome** or in your **Device**.

![Cordova SQLite](https://github.com/jdnichollsc/Ionic-Starter-Template/blob/gh-pages/images/sqlite.png?raw=true)

* **Debug in the browser:** Test using the **`./app/js/queries.js`** file to create your queries **(Drop tables, create tables, insert data, etc)**.
* **Debug in the device:** Test using the **`./www/pre.db`** file, you can edit the database using **[DB Browser for SQLite](http://sqlitebrowser.org/)**

##SQLite examples using **Angular Services**
* Returns the first element in a sequence that satisfies a specified condition, throws an exception if no matching element is found in source:
```javascript
var query = "SELECT * FROM Users WHERE Name LIKE '%?%'";
return $q.when($sqliteService.getFirstItem(query, ['Juan']));
```
* Returns the first element of a sequence that satisfies a specified condition, or a default value if the sequence contains no elements:
```javascript
var query = "SELECT * FROM Users WHERE Name LIKE '%?%'";
return $q.when($sqliteService.getFirstOrDefaultItem(query, ['Juan']));
```
* Returns all the elements of a sequence that satisfies a specified condition:
```javascript
var query = "SELECT * FROM Users WHERE Name LIKE '%?%'";
return $q.when($sqliteService.getItems(query, ['Juan']));
```
* Execute a SQL query:
```javascript
var query = "DELETE FROM Users WHERE Name LIKE '%?%'";
return $q.when($sqliteService.executeSql(query, ['Juan']));
```

###**Note**: If you don't want to use SQLite, you must perform the following steps:
1. Remove **`./www/pre.db`** file.
2. Remove **`./app/js/queries.js`** file.
3. Remove **`./app/js/services/sqlite.js`** file.
4. Uninstall the plugin using the CLI: **`ionic plugin rm cordova-sqlite-ext --save`**
5. Remove the following line from **`./app/js/app.js`** file:
```javascript
$sqliteService.preloadDataBase(true);
```

#Ionic Tips
* Ionic View LifeCycle: More **[here](http://www.gajotres.net/understanding-ionic-view-lifecycle/)**
```javascript
$scope.$on('$ionicView.beforeEnter', function(){
  alert("Before to enter to the view");
});
$scope.$on('$ionicView.afterEnter', function(){
  alert("After to enter to the view");
});
```
* Reload the current state:
```javascript
$state.go($state.current, {}, {reload: true});
```
* Disable the back option before to navigate to other state:
```javascript
$ionicHistory.nextViewOptions({
    disableBack: true,
    disableAnimate : true,
    historyRoot  : true
});
```
* Clear the cache:
```javascript
$ionicHistory.clearCache();
```
* Clear the history:
```javascript
$ionicHistory.clearHistory();
```
* Change the direction before to navigate to other state:
```javascript
$ionicViewSwitcher.nextDirection('back');
```
* Navigate to other state:
```javascript
$state.go("app.login");
```
* Disable the drag to open the side menu:
```javascript
$ionicSideMenuDelegate.canDragContent(false);
```
* Check the current platform
```javascript
var deviceInformation = ionic.Platform.device();

var isWebView = ionic.Platform.isWebView();
var isIPad = ionic.Platform.isIPad();
var isIOS = ionic.Platform.isIOS();
var isAndroid = ionic.Platform.isAndroid();
var isWindowsPhone = ionic.Platform.isWindowsPhone();

var currentPlatform = ionic.Platform.platform();
var currentPlatformVersion = ionic.Platform.version();
```
* Disabling the tap system **(To disable the tap for an element and all of its children elements)**
```html
<div data-tap-disabled="true">
    <div id="google-map"></div>
</div>
```
* Using Ionic gestures with options from Angular Directives
```javascript
$ionicGesture.on('hold', function (e) {
  //Code...
}, element, { hold_threshold: 20 });
```
* Ionic trigger **[events](http://ionicframework.com/docs/api/utility/ionic.EventController/)**
```javascript
ionic.trigger("hold", { target: document.getElementsByClassName("item")[0] });
```
* Execute when device is ready
```javascript
ionic.Platform.ready(function(){
  //Code...
});
```

###**Global configuration**:
* Enable the native scrolling (Enable or Disable jsScrolling):
```javascript
$ionicConfigProvider.scrolling.jsScrolling(false);
```
* Set the Maximum number of view elements to cache in the DOM:
```javascript
$ionicConfigProvider.views.maxCache(5);
```
* Center align the title in the navBar:
```javascript
$ionicConfigProvider.navBar.alignTitle('center');
```
* Disable swipeback on iOS:
```javascript
$ionicConfigProvider.views.swipeBackEnabled(false);
```
* Set the back button text to empty:
```javascript
$ionicConfigProvider.backButton.previousTitleText(false).text('');
```
* Change Ionic gestures options:
```javascript
ionic.Gestures.gestures.Hold.defaults.hold_threshold = 20;
```
* Platform Customization

  Platform | CSS Class
  ------- | ------
  Browser | platform-browser
  Cordova | platform-cordova
  Webview | platform-webview
  iOS | platform-ios
  iPad | platform-ipad
  Android | platform-android
  Windows Phone | platform-windowsphone
  
  * Dynamically Loading Templates
  ```javascript
  .state('tab', {
    templateUrl: function() {
      if (ionic.Platform.isAndroid()) {
          return  "templates/home-android.html";
      }
      return "templates/home.html";
    }
  });
  ```

#Crosswalk
Improve the performance of your HTML, CSS, and JavaScript if is required.

Command | Action
------- | ------
`ionic browser list` | Show all the browsers available by platform
`ionic browser rm crosswalk` | Remove a browser
`ionic browser add crosswalk` | Install the Chromium browser for Android
`ionic browser add crosswalk@10.39.235.15` | Specifies a version of Chromium
`ionic browser add crosswalk-lite` | Install the Crosswalk lite version
`ionic browser revert android` | Remove any custom browser that was installed for the platform by replacing it with the system default browser

#npm commands
Command | Action
------- | ------
`npm i ionic cordova bower gulp -g` | Install Ionic, Cordova, Bower and Gulp packages globally 
`npm cache clean` | Remove the cache to force update the packages. Useful to solve npm issues using the CLI.

#Ionic commands

Command         | Action
-------------   | -------------
`ionic login`   | To get logged in the CLI and use the Ionic services
`ionic upload`  | Upload your app to Ionic repository and debug remotely (Your clients) using the useful **[Ionic View App](http://view.ionic.io/)** 
`ionic serve`   | Test on the browser
`ionic serve --lab` | Test on the browser iOS and Android version 
`ionic lib update`  | Update Ionic library files
`ionic resources`   | Generate icons and splash screens. The images are located in `./resources/` directory. More info **[here](http://ionicframework.com/docs/cli/icon-splashscreen.html)**.
`ionic resources --icon` | Generate only the icons. `icon.png`, `icon.psd` or `icon.ai` is located in `./resources/` directory
`ionic resources --splash` | Generate only the splash screens. `splash.png`, `splash.psd` or `splash.ai` is located in `./resources/` directory
`ionic resources ios --icon` | Generate icons per platform

#Cordova commands

Command         | Action
--------------- | -----------
cordova platform add `android` | Add the platform to build your app. `android - ios - windows`
cordova platform rm `android` | Remove the platform
cordova plugin add `git_url` --save | Add a plugin to use native capabilities. `Native Devs are your friends`
cordova plugin list | See the plugins that you're using. Find more **[here!](https://cordova.apache.org/plugins/)**
cordova plugin rm `plugin_name` --save | Remove a plugin
cordova build windows -- --appx=8.1-win --archs="x86" | Build the app to Windows (Open the Solution `platforms/windows/*.sln` on **[Visual Studio](https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx)**)

#Tools

Name            | Description
--------------- | -----------
**[Visual Studio Code](https://code.visualstudio.com/)** | Build and debug your app using a [extension](https://marketplace.visualstudio.com/items?itemName=vsmobile.cordova-tools)
**[GapDebug](https://www.genuitec.com/products/gapdebug/)** | Only debug in the device
**[GenyMotion](https://www.genymotion.com/)** | Better Android Emulation

#Visual Studio Code commands and shortcuts
Command/Shortcut        | Action
--------------- | --------------
`code .` | Open the editor from CLI
`F1` | Open the `Command Palette`
`Ctrl + Shift + N` | Open other Visual Studio Code instance
`Ctrl + }` | Toogle comment code
`Ctrl + ñ` | Open the Integrated Terminal

#Sign to Android (Commands)

1. `cordova build --release android`
2. `keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000`
3. `jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore HelloWorld-release-unsigned.apk alias_name`
4. `zipalign -v 4 HelloWorld-release-unsigned.apk HelloWorld.apk`

#Links

* **[Market place](http://market.ionic.io/)**
* **[Facebook group](https://www.facebook.com/groups/phonegapcordova/)**
* **[Codepen](http://codepen.io/ionic/pens/public/?grid_type=list)**
* **[Spanish Presentation](http://slides.com/juandavidnicholls/apps-moviles)**
* **[Ionic CLI](https://github.com/driftyco/ionic-cli)**
* **[Ionic Framework Examples](https://gist.github.com/jdnichollsc/53bfd200f04fd51c87d5)**
* **[Ionic Services](http://docs.ionic.io/)**

![Your code is mine!](https://github.com/jdnichollsc/Ionic-Starter-Template/blob/gh-pages/images/obfuscate.png?raw=true)

# Happy coding
Made with <3

<img width="150px" src="http://phaser.azurewebsites.net/assets/nicholls.png" align="right">
