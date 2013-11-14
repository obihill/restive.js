# Device.JS Plugin

The Web today is [Restive](http://blog.devicejs.com/posts/3695313/restive-web-design)! Device.JS Plugin is a JQuery Plugin that helps you quickly and easily add features to your Web Site that enable it respond and adapt to virtually every Web-enabled Device. Using a combination of Device Detection, Advanced Breakpoints Management, and Orientation Management, the Plugin will give your Web site an uncanny ability to stay robust in the face of a constantly changing device landscape.


## Why Device.JS Plugin?!

As a Web Designer, designing Web sites for the Personal Computer and for Mobile Devices is enough work already. You can design all your layouts using HTML and CSS, but enabling your Web sites to be Responsive/Adaptive usually requires a lot more work than is reasonable. 

If you find that you fit one or more of the criteria below, then you might want to consider using Device.JS Plugin:

- You design Web Sites that need to be Responsive or Adaptive
- You are not completely satisfied with the tools and/or approaches you currently use to achieve this "Responsiveness" or "Adaptiveness"
- You need ONE solution and do not want (nor have the time) to cobble together multiple polyfills to enable these desired features
- You need more functionality than CSS Media Queries can possibly provide at the moment
- You need a solution that you can truly 'Set-and-Forget'
- You need a solution that is very easy to understand, use, and maintain



## Requirements

- [jQuery](http://jquery.com/) (>= 1.7.1 is recommended)



## Versions

There are two versions of the Device.JS Plugin:

1. Basic Version: this is the version available here on Github
2. Pro Version: this is available exclusively via the [Device.JS Plugin Web Site](http://plugin.devicejs.com)



## License

[Click here to view the License Agreement](/LICENSE.md) for the Basic Version of Device.JS Plugin.

Please note that Device.JS Plugin Basic is **FREE** (and always will be) for Non-Commercial and Personal Projects. If you plan to use Device.JS Plugin Basic in a Commercial context, you will need to purchase a Basic Commercial License. Pay Once, Use Forever #POUF.

[![Buy Basic Commercial License](/img_button_buynow_djsp_pouf_github.png)](https://devicejs.dpdcart.com/cart/buy?product_id=58953&product_price_id=60074&quantity=1&gateway=creditcard)

Use Coupon Code **GITHUB** to get 20% off Original License Price. Valid for first 1,000 users.

[Click here for more information on what is considered **Commercial**](/WHAT-IS-COMMERCIAL.md)


## Changelog

[Click here to view the Changelog](/CHANGELOG.md)



## Installation

Include script *after* the jQuery library:

```html
<script src="/path/to/jquery.min.js"></script>
<script src="/path/to/device.min.js"></script>
```    


## Usage

The basic format for using Device.JS Plugin is as follows:

```javascript
<script>
    $(document).ready(function () {
        $('selector').devicejs(options);
    });
</script>
```

Let's try a basic example. Say we have designed a HTML5 Web site and we want to make it Responsive to a specific set of breakpoints: 240, 320, 480, 640, 960, 1024, and 1280. Our Device.JS Plugin Setup will look something like this:

```javascript
<script>
    $(document).ready(function () {
        $('body').devicejs({
			breakpoints: ['240', '320', '480', '640', '960', '1024', '1280'],
            classes: ['css-240', 'css-320', 'css-480', 'css-640', 'css-960', 'css-1024', 'css-1280']            
		});
    });
</script>
```

**So what does the above setup mean?!** The Plugin will actively monitor the viewport of any devices that visit your web site for the following width ranges: 0 to 240 pixels, 241 to 320 pixels, 321 to 480 pixels, 481 to 640 pixels, 641 to 960 pixels, 961 to 1024 pixels, and 1025 to 1280 pixels. If the viewport of the device is between 0 and 240 pixels wide, the plugin will add the class `css-240` to the `<body>` tag; if the viewport is between 241 and 320 pixels wide, it will add the class "css-320", and so on.

So if I have a Google Nexus 4 (768 pixels wide by 1280 pixels high when in portrait orientation) and I visited a Web site with the above Device.JS Plugin configuration, the plugin would add the class `css-960` to the body tag, because the viewport falls within 640 pixels and 960 pixels wide. You could then tweak your CSS file and add any required rules required to customize your layout.

**NOTE**: We strongly advise that you use either `html` or `body` as your preferred selector always.



## API Reference

### Options

These are the options available within **Device.JS Plugin**. The default values are also listed.


#### breakpoiints

An itemized list of dimensions that define a specific range within which an adaptive action should take place. Device.JS Plugin allows for 2 distinct types of breakpoints:

1. Pixel e.g. 320 pixels
2. Resolution e.g. nHD, SVGA, XGA, etc.

Breakpoints are defined as an array:

```javascript
    //example
    breakpoints: ['240', '320', '480', '640']
```

The above setting means that the plugin will monitor the viewport for the following width ranges: 0 to 240px, 241 to 320 pixels, 321 to 480 pixels, and 481 to 640 pixels. It will then apply classes (see next option) to the DOM based on which range the viewport width matches.

**NOTE**: Do not start from zero when defining breakpoints. Always start from the upper limit of the implied range. For example, if you specify '240' as the first item in the breakpoints option, the plugin will enable a range of 0 to 240; if 480 is the next item, the plugin will enable a range of 241 to 480 and so on.

**NOTE**: Ensure that you define your breakpoints based on device pixels [and not css pixels]. For example, if you want to match a device width of 720 pixels, use `720` even when you know the Device-Independent Pixel Width is `360`. DO NOT use Device-Independent (CSS) pixel values to define `breakpoints`.


#### classes

An itemized and corresponding list of CSS classes that will be set to the matched element defined in the Device.JS Plugin selector, in lock-step with the corresponding breakpoints.

Classes are defined as an array:

```javascript
    //example
    classes: ['240-c', '320-c', '480-c', '640-c']
```

The above setting will add the class `320-c` to the selected DOM element when the viewport is between 241 and 320 pixels (considering the breakpoints options defined earlier).

**NOTE**: The number of classes defined here must be identical to the number of breakpoint items defined in the `breakpoints` option.

**NOTE**: You can also add multiple classes to the matched element defined in the Device.JS Plugin selector. Simply space-separate your classes e.g. ‘myclass1 myclass2’


#### platform

This defines the specific device platform that you want to target. The following values are available for use:

- `all`: target all platforms. This is the default setting.
- `ios`: target only devices based on the iOS platform e.g. iPad, iPod, etc.
- `android`: target only devices based on the Android platform e.g. Samsung Galaxy S4, Amazon Kindle, etc.
- `symbian`: target only devices based on the Symbian platform e.g. Nokia Asha 311
- `blackberry`: target only devices based on the Blackberry platform e.g. Blackberry Q10
- `windows`: target only devices based on the Windows platform e.g. Nokia Lumia, Microsoft Surface, etc.

```javascript
    //example
    platform: 'android'
```


#### formfactor

This defines the specific form factor that you want to target. The following values are available for use:

- `all`: target all devices. This is the default setting.
- `pc`: target all Personal Computers (e.g. PC, Mac, Linux, etc.)
- `tv`: target smart TVs and Game Consoles
- `tablet`: target tablet devices
- `phone`: target phones


#### turbo_classes

There are certain instances when you need to define a class that will be added to your selected DOM element alongside any other classes you may have defined in `classes`. 

For example, let's say you want to add a class `mobi` if the device is a mobile device alongside the selected class previously defined in the `classes` option. You can do this quite easily using `turbo_classes`.

Using `turbo_classes`, you can specify one or more conditions and a corresponding class for each condition that will be added to your DOM selector when said condition is met.

You define your turbo class (or classes) in the following format: `{condition}={class}`

Where `<condition>` is the specific circumstance that will trigger the `<class>` to be added. The following `<condition>` definitions are available for use:

- `is_mobile`: will add a `<class>` if device is mobile
- `is_non_mobile`: will add a `<class>` if device is non-mobile
- `is_retina`: will add a `<class>` if device has a "Retina" display
- `is_phone`: will add a `<class>` if device is a phone
- `is_tablet`: will add a `<class>` if device is a tablet
- `is_tv`: will add a `<class>` if device is a tv
- `is_pc`: will add a `<class>` if device is a personal computer
- `is_portrait`: will add a `<class>` if device is in portrait orientation
- `is_landscape`: will add a `<class>` if device is in landscape orientation

So let's further clarify with an illustration:

```javascript
<script>
    $(document).ready(function () {
        $('body').devicejs({
            breakpoints: ['320', '480', '640', '720', '960', '1280'],
            classes: ['320-c', '480-c', '640-c', '720-c', '960-c', '1280-c'],
            turbo_classes: 'is_mobile=mobi,is_portrait=view-p'
        });
    });
</script>
```

**Explanation**: The class in the `classes` option will be added to the `<body>` tag depending on which breakpoint range matches the device viewport. However, since the `turbo_classes` option is defined with two conditions, the following will happen:

1. If the device is a mobile device, `mobi` will be added to the `<body>` tag class attribute
2. If the device is in portrait orientation, `view-p` will be added to the `<body>` tag class attribute.

So if the device is in portrait, and is 640 pixels wide, `mobi view-p 640-c` will be added to the `class` attribute of the `<body>` tag.
 
**Note**: You can use `turbo_classes` to add only one class per condition i.e. multiple class definitions per condition are not possible. So that means you can't do something like this: `turbo_classes: 'is_mobile=mobi,is_mobile=mobi_plus'`



### Methods

These are the methods available within **Device.JS Plugin**. A usage example is also listed.


#### getPlatform

This determines the operating platform of the device. The following are the possible results when using this method: `ios`, `android`, `symbian`, `blackberry`, `windows`. If the device is not recognized as one of these platforms, `other` will be returned.

```javascript
    //example
    var platform = $.devicejs.getPlatform();
```


#### getFormFactor

This determines the form-factor of the device. There are only four possible results: `phone`, `tablet`, `tv`, `pc`. If none of the first three are detected, it will be assumed that the device has a `pc` form-factor.

```javascript
    //example
    var formfactor = $.devicejs.getFormFactor();
```


#### getResolution

This determines the standard graphic display resolution of the device e.g. `VGA`, `SVGA`, `qHD`, etc.

```javascript
    //example
    var res = $.devicejs.getResolution();
```


#### getOrientation

This determines the currently active device orientation. There are only two possible results are `portrait`, and `landscape`.

```javascript
    //example
    var ort = $.devicejs.getOrientation();
```


#### getPixelRatio

This determines the pixel ratio of the device.

```javascript
    //example
    var pxr = $.devicejs.getPixelRatio();
```


#### getViewportW: 

This determines the device viewport width [in device pixels].

```javascript
    //example
    var viewport_w = $.devicejs.getViewportW();
```


#### getViewportH: 

This determines the device viewport height [in device pixels].

```javascript
    //example
    var viewport_h = $.devicejs.getViewportH();
```


#### getScreenW: 

This determines the device screen width.

```javascript
    //example
    var screen_w = $.devicejs.getScreenW();
```


#### getScreenH: 

This determines the device screen height.

```javascript
    //example
    var screen_h = $.devicejs.getScreenH();
```


#### getPixelW: 

This determines the device viewport width [in device-independent pixels].

```javascript
    //example
    var css_pixel_w = $.devicejs.getPixelW();
```


#### getPixelH: 

This determines the device viewport height [in device-independent pixels].

```javascript
    //example
    var css_pixel_h = $.devicejs.getPixelH();
```


#### isMobile

This determines whether a device is a mobile device. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_mobile = $.devicejs.isMobile();
```


#### isNonMobile

This determines whether a device is not a mobile device. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_non_mobile = $.devicejs.isNonMobile();
```


#### isPhone

This determines whether a device is a Phone. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_a_phone = $.devicejs.isPhone();
```


#### isTablet

This determines whether a device is a Tablet. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_a_tablet = $.devicejs.isTablet();
```


#### isTV

This determines whether a device is a TV or TV-enabled device. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_a_tv = $.devicejs.isTV();
```


#### isPC

This determines whether a device is a Personal Computer. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_a_pc = $.devicejs.isPC();
```

**NOTE**: A `pc` [in the context of Device.JS Plugin] is basically any device that is not a `phone`, `tablet`, or `tv`.


#### isIOS

This determines whether a device is based on the iOS Platform. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_ios = $.devicejs.isIOS();
```


#### isAndroid

This determines whether a device is based on the Android Platform. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_android = $.devicejs.isAndroid();
```


#### isSymbian

This determines whether a device is based on the Symbian Platform. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_symbian = $.devicejs.isSymbian();
```


#### isBlackberry

This determines whether a device is based on the Blackberry Platform. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_blackberry = $.devicejs.isBlackberry();
```


#### isWindows

This determines whether a device is based on the Windows Platform. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_windows = $.devicejs.isWindows();
```

**NOTE**: This method will detect both Windows Phones and Tablets.


#### isWindowsPhone

This determines whether a device is based on the 'Windows Phone' Platform. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_windows_phone = $.devicejs.isWindowsPhone();
```

**NOTE**: This method will detect only Windows Phones.


#### isRetina

This determines whether a device has a 'Retina' display i.e. a display with a pixel ratio equal to or greater than 2. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_retina = $.devicejs.isRetina();
```


#### isPortrait

This determines whether a device is in Portrait Orientation mode. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_portrait = $.devicejs.isPortrait();
```


#### isLandscape

This determines whether a device is in Landscape Orientation mode. Returns `true` if so, `false` if otherwise.

```javascript
    //example
    var is_device_landscape = $.devicejs.isLandscape();
```


### Event Callbacks

These are technically also JQuery plugin options. However, just for lucidness we have separated them from **Options** above.

The following Callbacks are available for use in **Device.JS Plugin**


#### onReady

This callback is triggered on Plugin initialization i.e when the web page is loaded.

```javascript
	$('body').devicejs({
		onReady: function(){alert("I'M READY WHEN YOU ARE!");}
	});
```


#### onResize

This callback is triggered after there is a change in the size of the Viewport.

```javascript
	$('body').devicejs({
		onResize: function(){alert("I JUST GOT RESIZED!");}
	});
```

**NOTE**: This callback does not work on mobile devices i.e. `phone` and `tablet`


#### onRotate

This callback is triggered just after the Device Orientation changes i.e. from Portrait to Landscape and vice versa.

```javascript
	$('body').devicejs({
		onRotate: function(){alert("I JUST GOT ROTATED!");}
	});
```


#### onRotateToP

This callback is triggered just after the Device Orientation changes from Landscape to Portrait.

```javascript
	$('body').devicejs({
		onRotateToP: function(){alert("I JUST GOT ROTATED TO PORTRAIT!");}
	});
```


#### onRotateToL

This callback is triggered just after the Device Orientation changes from Portrait to Landscape.

```javascript
	$('body').devicejs({
		onRotateToL: function(){alert("I JUST GOT ROTATED TO LANDSCAPE!");}
	});
```

#### onRetina

This callback is triggered if the Device has a pixel ratio of 2 or higher.

```javascript
	$('body').devicejs({
		onRetina: function(){alert("I CANNOT BE MORE CLEAR-EYED!");}
	});
```


#### onPortait

This callback is triggered if the Device is in Portrait Orientation on initialization i.e. when the web page is loaded.

```javascript
	$('body').devicejs({
		onPortrait: function(){alert("I AM TALLER THAN I AM WIDE!");}
	});
```


#### onLandscape

This callback is triggered if the Device is in Landscape Orientation on initialization i.e. when the web page is loaded.

```javascript
	$('body').devicejs({
		onLandscape: function(){alert("I AM WIDER THAN I AM TALL!");}
	});
```


#### onPhone

This callback is triggered if the Device is a Phone.

```javascript
	$('body').devicejs({
		onPhone: function(){alert("I AM A PHONE!");}
	});
```


#### onTablet

This callback is triggered if the Device is a Tablet.

```javascript
	$('body').devicejs({
		onTablet: function(){alert("I AM A TABLET!");}
	});
```


#### onTV

This callback is triggered if the Device is a TV or TV-enabled e.g. game console.

```javascript
	$('body').devicejs({
		onTV: function(){alert("I AM A TELEVISION!");}
	});
```


#### onPC

This callback is triggered if the Device is a Personal Computer i.e. not a Phone, Tablet, or TV.

```javascript
	$('body').devicejs({
		onPC: function(){alert("I AM NOT A PHONE, TABLET, OR TV!");}
	});
```


#### onMobile

This callback is triggered if the Device is a Mobile Device i.e. Phone or Tablet.

```javascript
	$('body').devicejs({
		onMobile: function(){alert("I AM MOBILE!");}
	});
```


#### onNonMobile

This callback is triggered if the Device is a Non-Mobile Device i.e. TV or PC.

```javascript
	$('body').devicejs({
		onNonMobile: function(){alert("I AM NOT MOBILE!");}
	});
```


#### onAddClass

This callback is triggered when the Device.JS Plugin adds a class to the DOM element identified in `selector` i.e. when a breakpoint is matched. The name of the class added is passed as the only argument of this function.

```javascript
	$('body').devicejs({
		onAddClass: function(name){alert("PLUGIN JUST ADDED A CLASS CALLED '"+name+"'!");}
	});
```


#### onRemoveClass

This callback is triggered when the Device.JS Plugin removes a class from the DOM element identified in `selector` i.e. when there is no breakpoint match. The name of the class removed is passed as the only argument of this function.

```javascript
	$('body').devicejs({
		onRemoveClass: function(name){alert("PLUGIN JUST REMOVED A CLASS CALLED '"+name+"'!");}
	});
```



## Special Features


### Orientation Markers

Orientation markers are a special feature of Device.JS Plugin that allows you to define breakpoints that target viewport width ranges in specific orientation modes. For example, if you define the following breakpoints: 240, 360-l, 480-p; the Plugin will target the following viewports: 0 to 240 pixels, 241 to 360 pixels only if the device is in landscape orientation, and 361 to 480 pixels only if the device is in portrait orientation. You can append an orientation marker to any breakpoint that you have defined. 

Supported Orientation Markers are:

- `-p` for portrait orientation
- `-l` for landscape orientation

**NOTE**: Orientation markers always take precedence if duplicate breakpoints are defined. For example, let's say you have defined breakpoints that include `640` and `640-p`, with corresponding classes `640-c` and `640-pc` respectively. If the device viewport width falls within 0 and 640 pixels, the class `640-pc` will be applied even though the two breakpoints are both technically an exact match.

**NOTE**: Orientation markers work a little differently when using Resolution Breakpoints. When using resolution breakpoints with orientation markers, Device.JS Plugin uses the width component of the resolution when in portrait, and the height component of the resolution when in landscape. For example, let's say you define the following: hvga, hvga-l; this resolution is 320px by 480px. The Plugin will target 0 to 320 pixels, and 321 to 480 pixels only if the device is in landscape orientation.

**NOTE**: If you define two identical breakpoints with two identical orientation markers, the one that appears first in your definition will take precedence.


### Multiple Constructor Usage

Device.JS Plugin lets you call its constructor multiple times. The primary reason for doing this is when you want to segment your breakpoints e.g. when you want to target multiple platforms or form-factors.

The syntax for using multiple constructors is as below:

```javascript
    $.devicejs.startMulti();
    
	$('selector').devicejs(options_1);
    $('selector').devicejs(options_2);
    
	$.devicejs.endMulti();
```

So considering a real example, let's say we need to define multiple breakpoints for two different form-factors. We can do this as follows:

```javascript
    $.devicejs.startMulti();
    
	$('body').devicejs({
	    breakpoints: ['240', '360', '480', '640', '960', '1280'],
        classes: ['240-cp', '360-cp', '480-cp', '640-cp', '960-cp', '1280-cp'],		
		formfactor: 'phone'
	});
		
	$('body').devicejs({
	    breakpoints: ['240', '360', '480', '640', '960', '1280'], 
		classes: ['240-ct', '360-ct', '480-ct', '640-ct', '960-ct', '1280-ct'],		
		formfactor: 'tablet'
	});
	
	$.devicejs.endMulti();
```

Doing the above allows you to 

**NOTE**: You must always call the method `$.devicejs.startMulti()` before you define multiple constructors, and `$.devicejs.endMulti()` at the very end. If you don't, you'll get errors.

**NOTE**: Ensure that you use the same selector for each constructor i.e. if you're using 'body' as your selector for the `<body>` tag, make sure you use that selector for all your constructor calls. This is best practice advice.

**NOTE**: You should only use this feature when you want to segment breakpoints along platform or form-factors i.e. you want to define different breakpoints for different platforms or form-factors. You shouldn't use it as a way of adding more breakpoints (if you want to add more breakpoints, just add them to your existing breakpoints). We've built Device.JS Plugin to work even if you use multiple constructors without specifying segmentation options like `platform` and `formfactor`, but you really shouldn't use it that way ok?! #FingerWag



## Known Limitations

- This plugin uses AmplifyJS Store functionality to store data in SessionStorage (by default and if available). If SessionStorage is not available, LocalStorage is used; And if Session Storage and LocalStorage are not available, it relies on AmplifyJS Store to make a suitable selection. As a result, behavior on very old browsers may be unpredictable.  



## Script Reference Warnings

Please be mindful to disable the following Javascript libraries from your Web pages before using Device.JS Plugin (i.e. if you have them enabled):

- [AmplifyJS Store](http://amplifyjs.com/api/store/)
- [JSON2.js](https://github.com/douglascrockford/JSON-js)
- [jquery-cookie](https://github.com/carhartl/jquery-cookie)
- [iOS-Orientation-Fix](https://github.com/PeterWooster/iOS-Orientationchange-Fix)

These libraries are already embedded within Device.JS Plugin.


## Credits

Device.JS will like to thank the following third-parties for script usage:

- AppendTo - [AmplifyJS Store](http://amplifyjs.com/api/store/)
- Douglas Crockford - [JSON2.js](https://github.com/douglascrockford/JSON-js)
- Kevin van Zonneveld - [PHPJS](https://github.com/kvz/phpjs)
- Klaus Hartl - [JQuery Cookie](https://github.com/carhartl/jquery-cookie) 
- Scott Jehl, Peter Wooster - [iOS-OrientationChange-Fix](https://github.com/PeterWooster/iOS-Orientationchange-Fix)

And Special Thanks for inspiration

- Ryan Van Etten - [Response.js](https://github.com/ryanve/response.js)

