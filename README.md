# Angular Material-Start (Tutorials)

This branch contains the tutorial steps and processes used to implement the start-app shown below:

![material-starter-ux2](https://cloud.githubusercontent.com/assets/210413/6448551/70864488-c0e0-11e4-8767-c4e1e4c2f343.png)

Above is a snaphot of the Starter-App with a **Master-Detail** layout: showing a list of users (left) and a user detail view (right). 

Also shown is the user experience that will be displayed for smaller device sizes. The responsive layout reveals the **menu** button that can be used to hide the user list and a **share** button that can be used to show the Share bottom sheet view.

This Starter app demonstrates how:

*  Angular Material `layout` and `flex` options can easily configure HTML containers
*  Angular Material components `<md-toolbar>`, `<md-sidenav>`, `<md-icon>` can be quickly used
*  Custom controllers can use and show `<md-bottomsheet>` with HTML templates
*  Custom controller can easily, programmatically open & close the SideNav component.
*  Responsive breakpoints and `$mdMedia` are used
*  Theming can be altered/configured using `$mdThemingProvider`


This sample application is purposed as both a learning tool and a skeleton application for a typical [AngularJS Material](http://material.angularjs.org/) web app: comprised of a Side navigation area and a content area. You can use it to quickly bootstrap your angular webapp projects and dev environment for these
projects.

<br/>
- - -

#### "How to build an App"

Here are some generalized steps that may be used to conceptualize the application implementation process:

1. Plan your layout and the components you want to use; preferrably with a site UX design document.
2. Use hard-coded HTML and mock content to make sure the components render as desired
3. Integrate UI components to your custom application logic
> Use the seamless integration possible with Angular directives and controllers<br/>
> This integration assumes that you have unit tested your app logic
4. Add Adaptive breakpoints
5. Add Theming support
6. Confirm ARIA compliance
7. Write e2e Tests 
> It is important to validate your app logic with Angular Material UI components.

<br/>
###### Wirefame 

The illustration below shows how we planned the layout and identified the primary components that will be used in the Starter application:

<br/>
![plancomponents2](https://cloud.githubusercontent.com/assets/210413/6444676/c247c8f8-c0c4-11e4-8206-208f55cbceee.png)

> Note: that container #2 (above) is a simple `<div>` container and not an Angular Material component.

<br/>
- - -

##### ES5 Tutorials

These tutorials assume that you have already cloned the repository and executed the `npm install` command.

You will notice html Tutorials #0 thru #8: these will be used to guide you through the development process. By following these tutorials stages, you will be very quickly introduced to the powerful features of Angular Material.

Each tutorial presents the resulting changes for that stage. It is recommended, however, that you start with the preceding tutorial and manually make the changes requested. The effort you invest to implement these changes will highlight specific concepts at each Tutorial stage.

> At each tutorial stage, you should use a web-server to view the that tutorial page. Open the dev console to see any warnings and browser the elements.

<br/>
- - -

### Step #1: Load Libraries

Here you modified the shell application [available in `tutorial_0.html`] to use Angular-Material.

> ##### Live JSBin Demo for [Step #1](http://thomasburleson.jsbin.com/fuyomo/edit?html,output)

* Use Bower to install angular-material with `bower install angular-material -D`
* In the HTML, load the CSS and JS modules:
* Configure the app dependency on 'ngMaterial'

```html
  <head>
    <link href="./bower_components/angular-material/angular-material.css" rel="stylesheet" />
  </head>

  <body>
    <script src="./bower_components/angular/angular.js" type="text/javascript" ></script>
    <script src="./bower_components/angular-animate/angular-animate.js" type="text/javascript" ></script>
    <script src="./bower_components/angular-aria/angular-aria.js" type="text/javascript" ></script>
    <script src="./bower_components/angular-material/angular-material.js" type="text/javascript" ></script>

	<script>
		// Include the dependency upon ngMaterial - important !!
		angular.module('starterApp', ['ngMaterial']);
	</script>
  </body>
```

<br/>
- - -

### Step #2: Container Layouts

Here you used the wireframe planning and layout to identify the components and attributes needed. Then use the Angular Material Layout api to layout your containers and responsively adjust their sizes.

> ##### Live JSBin Demo for [Step #2](http://thomasburleson.jsbin.com/kesaci/edit?html,output)

![Step #2: Containers with the Layout API](https://cloud.githubusercontent.com/assets/210413/12570184/079aaf72-c39b-11e5-8403-794f2ff99787.png)

* Add the `<md-toolbar>`, `<md-sidenav>`, `<md-content>` containers
> Note: that the md-sidenav is the container the Users **master** list view, and the md-content is the container for the User **detail** view.
* Add the **layout** and **flex** attributes to configure the container layouts and sizing aspects.
* Use `md-locked-open` to lock the sidenav open on the left
* Use the `md-whiteframe-z2` to add a shadow the the sidenav

```html
  <body ng-app="starterApp" layout="column">

	<!-- Container #1 (see wireframe) -->
    <md-toolbar layout="row" >
      <h1>Angular Material - Starter App</h1>
    </md-toolbar>

	<!-- Container #2 -->
    <div flex layout="row">

		<!-- Container #3 -->
        <md-sidenav md-is-locked-open="true" class="md-whiteframe-z2"></md-sidenav>

		<!-- Container #4 -->
        <md-content flex id="content"></md-content>

    </div>
	
  </body>
```

<br/>
- - -

### Step #3: Hard-Coded HTML

Here you will use hard-coded elements and Angular Material UI componetns to render and layout each container's children elements.

> ##### Live JSBin Demo for [Step #3](http://thomasburleson.jsbin.com/bozasu/edit?html,output)

![tutorial_3](https://cloud.githubusercontent.com/assets/210413/12525866/89321b6c-c12d-11e5-9d0d-483725cc6de7.png)

* Show a list of Users in the `md-sideNav` container
  *  Use the `md-list`, `md-button`, and `md-icon` components with mock data
* Show mock user details in the `md-content` container

> Note: that the md-sidenav is the container for the **master** Users List view, and the md-content is the container for the **detail** User Detail view.



```html
  <body ng-app="starterApp" layout="column">

	<md-sidenav md-is-locked-open="true" class="md-whiteframe-z2">
	  <md-list>

		<!-- List item #1 -->
		<md-list-item >
			<md-button>
			  <md-icon md-svg-src="./assets/svg/avatar-1.svg" class="avatar"></md-icon>
			  Lia Luogo
			</md-button>
		</md-list-item>

		<!-- List item #2 -->
		<md-list-item >
			<md-button>
			 <md-icon md-svg-src="./assets/svg/avatar-4.svg" class="avatar"></md-icon>
			  Lawrence Ray
			</md-button>
		</md-list-item>

	  </md-list>
	</md-sidenav>

	<md-content flex id="content">
	  <!-- User details sample -->

	  <md-icon md-svg-src="./assets/svg/avatar-1.svg" class="avatar"></md-icon>
	  <h2>Lia Luogo</h2>
	  <p>
		I love cheese...
	  </p>
	</md-content>

  </body>
```

<br/>
- - -

### Step #4: Dynamic, Mock Data

Here you will replace the hard-coded HTML with dynamic, mock user data. Let's do this in 2 stages:

> ##### Live JSBin Demo for [Step #4](http://thomasburleson.jsbin.com/sabited/edit?html,js,output)

![tutorial_4](https://cloud.githubusercontent.com/assets/210413/12525864/87420d8a-c12d-11e5-8cd2-5d6d89c3309a.png)

  *  Build custom application logic for load the mock user data
  *  Build the HTML markup to render the dynamic, mock data

Then you integrate your custom, application logic.

* Define a Angular module 'users' for your custom code
* Define your data services, models, and controllers
* Load your custom code using script tags
* Configure your 'starterApp' to require (have a dependency upon) both 'ngMaterial' and 'users'.

```html
<script src="./src/users/Users.js"></script>
<script src="./src/users/UsersListController.js"></script>
<script src="./src/users/UsersDataservice.js"></script>

<script type="text/javascript">

  angular.module('starterApp', ['ngMaterial', 'users']);

</script>
```

Now replace the hardcoded HTML with dynamic markup using Angular directives (eg ng-repeat) 
and the standard Angular `{{ }}` interpolation markup.

* Use dynamic HTML that will be compiled and rendered by Angular
* Register a set of custom avatar icons; since each 'user' references an avatar ID.

```html
 <!-- Wireframe Container #2 -->
 <div flex layout="row">
 	<!-- Wireframe Container #3 -->
	<md-sidenav md-is-locked-open="true" class="md-whiteframe-4dp">
	  <md-list>
		<md-list-item ng-repeat="u in ul.users">
			<md-button ng-click="ul.selectUser(it)" ng-class="{'selected' : u === ul.selected }">
			  <md-icon md-svg-icon="{{u.avatar}}" class="avatar"></md-icon>
			  {{it.name}}
			</md-button>
		</md-list-item>
	  </md-list>
	</md-sidenav>

	<!-- Wireframe Container #4 -->
	<md-content flex id="content">
	  <md-icon md-svg-icon="{{ul.selected.avatar}}" class="avatar"></md-icon>
	  <h2>{{ul.selected.name}}</h2>
	  <p>{{ul.selected.content}}</p>
	</md-content>
	
 </div>


 <script type="text/javascript">
  angular
	  .module('starterApp', ['ngMaterial', 'users'])
	  .config(function( $mdIconProvider ){

		  // Register the user `avatar` icons
		  $mdIconProvider
				  .defaultIconSet("./assets/svg/avatars.svg", 128);
	  });
 </script>
```


<br/>
- - -

### Step #5: Use the BottomSheet 

In this step, you will use a dynamic, mbBottomSheet component at the bottom of the user details area. This contact sheet will be used to display user contact options available for each user.

> ##### Live JSBin Demo for [Step #5](http://thomasburleson.jsbin.com/kakezu/edit?html,css,js,output)

![tutorial_5](https://cloud.githubusercontent.com/assets/210413/12531590/303a3ee4-c1c4-11e5-954b-6d842ecc34c9.png)

*  create a "Share" button in the upper right of the user details view
*  create a [User Contact](https://github.com/angular/material-start/blob/es5-tutorial/app/src/users/view/contactSheet.html) view and controller to show in the bottom sheet
*  programmatically configure and load the bottomsheet using the $mdBottomSheet service
*  register icons that will be used inside the user ContactSheet

Add the `share` button to the UI:

```html
<md-content flex id="content">
  <md-icon md-svg-icon="{{ul.selected.avatar}}" class="avatar"></md-icon>
  <h2>{{ul.selected.name}}</h2>
  <p>{{ul.selected.content}}</p>

  <md-button class="share" md-no-ink ng-click="ul.makeContact(ul.selected)">
	<md-icon md-svg-icon="share"></md-icon>
  </md-button>
</md-content>

<script type="text/javascript">

  angular
	  .module('starterApp', ['ngMaterial', 'users'])
	  .config(function($mdIconProvider){

		  $mdIconProvider.icon("share", "./assets/svg/share.svg", 24);
	  });

</script>
```

Add the `makeContact()` function to the controller:

```js
/**
 * Show the bottom sheet
 */
function share(selectedUser) {

	$mdBottomSheet.show({
	  controllerAs     : "vm",
	  controller       : [ '$mdBottomSheet', ContactSheetController],
	  templateUrl      : './src/users/view/contactSheet.html',
	  parent           : angular.element(document.getElementById('content'))
	});

	 function ContactSheetController( $mdBottomSheet ) {
	   this.user = selectedUser;
	   this.items = [
		 { name: 'Phone'       , icon: 'phone'       , icon_url: 'assets/svg/phone.svg'},
		 { name: 'Twitter'     , icon: 'twitter'     , icon_url: 'assets/svg/twitter.svg'},
		 { name: 'Google+'     , icon: 'google_plus' , icon_url: 'assets/svg/google_plus.svg'},
		 { name: 'Hangout'     , icon: 'hangouts'    , icon_url: 'assets/svg/hangouts.svg'}
	   ];
	   this.contactUser = function(action) {
		 // The actually contact process has not been implemented...
		 // so just hide the bottomSheet

		 $mdBottomSheet.hide(action);
	   };
	 }
}
```

<br/>
- - -

### Step #6: Adaptive Layouts

Here you will add adaptive breakpoints so the application layout will adapt to different device display sizes.

> ##### Live JSBin Demo for [Step #6](http://thomasburleson.jsbin.com/zuzana/edit?html,css,js,output)

![tutorial_6](https://cloud.githubusercontent.com/assets/210413/12531596/5bae77c0-c1c4-11e5-8308-e6d955dffcb6.png)

* Lock the Users list open if device display is wider than > 600px; hide otherwise.
	* Use the `$mdMedia` to help with this feature.
* Hide the Toolbar menu icon button if the Users list is open.
* Add `click` support for the **menu** and **share** buttons.
	* Use the `$mdSideNav` service to toggle the sideNav
	* Auto-close the sideNav after a user is selected.


```html
<body>
	<!-- Wireframe Container #1 -->
    <md-toolbar layout="row">
	<md-button class="menu" hide-gt-sm ng-click="ul.toggleList()" >
        	<md-icon md-svg-icon="menu" ></md-icon>
    	</md-button>
    </md-toolbar>

	<!-- Wireframe Container #2 -->
	<div flex layout="row">

	 <!-- Wireframe Container #3 -->
	 <md-sidenav md-is-locked-open="$mdMedia('gt-sm')"
				 md-component-id="left">
	 </md-sidenav>

	 <!-- Wireframe Container #4 -->
	 <md-content flex id="content">
	  <md-button class="share" md-no-ink ng-click="ul.share(ul.selected)"></md-button>
	 </md-content>

	</div>
</body>
```

Register the **share** and **menu** icons displayed in the User Detail and Toolbar (respectively):

```html
<script type="text/javascript">

  angular
	  .module('starterApp', ['ngMaterial', 'users'])
	  .config(function($mdIconProvider){

		  $mdIconProvider
			  .icon("menu"       , "./assets/svg/menu.svg"        , 24)
			  .icon("share"      , "./assets/svg/share.svg"       , 24);
	  });

</script>
```

<br/>
- - -

### Step #7: Theming & ARIA

Here you will configure to use a different, darker theme.

> ##### Live JSBin Demo for [Step #7](http://thomasburleson.jsbin.com/lixohom/edit?html,css,js,output)

![tutorial_7](https://cloud.githubusercontent.com/assets/210413/12531597/686a3404-c1c4-11e5-8ca5-f62822ac12ab.png)

* Use `$mdThemingProvider` to configure a different theme using primary colors from the **brown** color palette and accent colors from the **red** color palette.


```html
<script type="text/javascript">

  angular
	  .module('starterApp', ['ngMaterial', 'users'])
	  .config(function($mdThemingProvider, $mdIconProvider){

		  $mdThemingProvider.theme('default')
			  .primaryPalette('brown')
			  .accentPalette('red');
	  });

</script>
```

Finally let's will fix any ARIA warnings that Angular Material may display in the Dev console.

* Insert `aria-label` attributes for mdButton components that do not have labels.

```html
<body>
	<!-- Wireframe Container #1 -->
    <md-toolbar layout="row">
      <md-button class="menu" aria-label="Show User List"></md-button>
    </md-toolbar>

	<!-- Wireframe Container #2 -->
	<div flex layout="row">

	 <!-- Wireframe Container #3 -->
	 <md-sidenav>...</md-sidenav>

	 <!-- Wireframe Container #4 -->
	 <md-content flex id="content">
	  <md-button class="share" aria-label="Share with {{ ul.selected.name }}"></md-button>
	 </md-content>

	</div>
</body>
```

<br/>
- - -


## Summary

With only seven (7) Tutorial Steps and a few minutes of work, we have quickly created a functional Angular Material application that is beautiful, responsive, theme'ed, accessible, and easily maintained. 

Imagine doing this without Angular Material!


