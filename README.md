# WiQuery for Apache Wicket

WiQuery is a project to simply Wicket integration with jQuery and jQuery UI.

This branch follows the development of Apache Wicket

WiQuery consists of 3 subprojects:
- core - the core library
- ui - Wicket components for JQuery UI components
- demo - examples

## Requirements

WiQuery requires the following:

- Java 8
- Servlet 5.0 
- Wicket 10 or newer

Newer or older major releases of Wicket are not compatible with this version of WiQuery.

## Migration from WiQuery 6.x

- You have to change the groupId of the dependency from `org.odlabs.wiquery` to `org.wicketstuff.wiquery`
- You have to change the version of your wiquery dependency to the current version that is compatible with your Wicket version. 
- You have to rename the imports for the WiQuery components because the Java package was renamed from `org.odlabs.wiquery` to `org.wicketstuff.wiquery`

## Projects

Below is a short description of the projects of WiQuery.

### WiQuery Core

The core project does not contain much:
 * some interfaces and classes which were used with Wicket before 6.0 and are now deprecated.
 * a basic classes to create events, mostly for jQuery UI.
 * a basic API to create javascript functions and options to be used in behaviors or events.

The jQuery javascript is not included in WiQuery but in Wicket. In order to use a specific version one can add the following code in their Application#init():

```java
getJavaScriptLibrarySettings().setJQueryReference(...);
```

or alternatively you can register a resource replacement:


```java
addResourceReplacement(JQueryResourceReference.get(), ...);
```

where ... is the instance of your resource reference.

### WiQuery JQuery UI

Here is where the fun starts, this project contains components and behaviors for enriching your application with jQuery UI.

One can override the default theme with a custom theme (for example 'foo') by creating a package called org.odlabs.wiquery.themes.foo and adding the following code in their Application#init():

```java
addResourceReplacement(WiQueryCoreThemeResourceReference.get(), new WiQueryCoreThemeResourceReference("foo"));
```
