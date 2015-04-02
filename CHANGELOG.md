# CHANGELOG
 
## 1.3.4
- Fix issue with turbo classes outputting function code with class names

## 1.3.3
- Fix issue with incomplete class additions when using multiple constructors

## 1.3.2
- Add additional viewport width test to better segment Windows Phones from Tablets
- Update similar viewport width test for Android to fix device class switching error 

 
## 1.3.1
- Fix issue where onAddClass callback fires of each resize event 
 
 
## 1.3.0
- Add two new options: `turbo_classes_reflow` and `turbo_classes_reflow_limits` for enabling layout reflow on PC devices when using `turbo_classes`
- Add two new callback functions: `onTurboClassReflow`, `onTurboClassReflowIn`, and `onTurboClassReflowOut`
- Solve issue with `$ is undefined` fatal error when JQuery is in noConflict mode


## 1.2.0
- Solve issue with `force_dip` option not working with `breakpoints`
- Solve issue with orientation status updates when soft-keyboard is initialized on certain mobile devices
- Solve issue with `turbo_classes` not being fired when `breakpoints` do not match 


## 1.1.0
- Solve Fatal Error and Storage Issue when using Private Browsing on iOS
- Add Modularity Feature
- Update Tablet Detection Feature for even Better Detection of Tablet Devices (especially for Android)


## 1.0.0
- Initial Release 
