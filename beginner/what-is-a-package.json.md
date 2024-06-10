# What is a package.json

* The package.json file in Node.js is the **heart of the entire application**.&#x20;
* It is basically the manifest file that contains the **metadata of the project**, where we **define the properties of a package**.



<figure><img src="../.gitbook/assets/Package.json" alt=""><figcaption><p>package.json</p></figcaption></figure>

### What's the difference between tilde(\~) and caret(^) in package.json?

See the [NPM docs](https://docs.npmjs.com/cli/v8/configuring-npm/package-json#dependencies) and [semver docs](https://docs.npmjs.com/cli/v6/using-npm/semver):

* `~version` **“Approximately equivalent to version”**, will update you to all future patch versions, without incrementing the minor version. `~1.2.3` will use releases from 1.2.3 to <1.3.0.
* `^version` **“Compatible with version”**, will update you to all future minor/patch versions, without incrementing the major version. `^2.3.4` will use releases from 2.3.4 to <3.0.0.
