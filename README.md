# PackageSetUpExample

First of all, to edit a package you need the repo. For this example, I created a new one.

![repo](Docs/Imgs/2019-11-07%2014_39_17-WhateverDevs_PackageSetUpExample_%20Example%20package%20for%20Unity..png)

The next step is to create a unity project to develop the package in. This project could also be a dev repo or something, but it shouldn't be necessary as all logic goes in the package.

![project](Docs/Imgs/2019-11-07%2014_43_04-Unity%20Hub%202.1.3.png)

After that, clone the repo of the package you want to edit into the packages folder of that project. It should look similar to this:

![cloned](Docs/Imgs/2019-11-07%2014_45_28-Packages.png)

For Unity to recognize the package, create a package.json file on the root of the package. The file in this project is a good example of a barebones package.json file.

After creating the package.json file, Unity should recognize the package and show it on the packages folder as well as on the package manager with the "development" tag. When a package is recognized as development, it means that it can be edited. A normal package in Unity is read-only.

![package-recognized](Docs/Imgs/2019-11-07%2014_48_50-Mail.png)

You can now edit the package and make the changes you need to make. Then commit and push (or do whatever branch-PR flow you do).

To publish the package, login to our registry with (creating a user for the registry is another story):

```
npm login --registry http://upm.rodrigovarga.com
```

After logging in, make sure your console is on the package root and run the command:

```
npm publish --registry http://upm.rodrigovarga.com
```

And that's it, the package is published.

To use the packages of that registry on a Unity project, enter the Scoped Registry adding the following to the manifest.json of that project.

````json
"scopedRegistries": [
    {
      "name": "Whatever Devs",
      "url": "http://upm.rodrigovarga.com",
      "scopes": [
        "whateverdevs"
      ]
    }
  ]
````

After that, Unity should show the packages of that scope (whateverdevs) on the package manager:

![manage](Docs/Imgs/2019-11-07%2015_39_12-Test%20-%20SampleScene%20-%20PC,%20Mac%20&%20Linux%20Standalone%20-%20Unity%202019.2.11f1%20_DX11_.png)