# api documentation for  [favicons-webpack-plugin (v0.0.7)](https://github.com/jantimon/favicons-webpack-plugin)  [![npm package](https://img.shields.io/npm/v/npmdoc-favicons-webpack-plugin.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-favicons-webpack-plugin) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-favicons-webpack-plugin.svg)](https://travis-ci.org/npmdoc/node-npmdoc-favicons-webpack-plugin)
#### Let webpack generate all your favicons and icons for you

[![NPM](https://nodei.co/npm/favicons-webpack-plugin.png?downloads=true)](https://www.npmjs.com/package/favicons-webpack-plugin)

[![apidoc](https://npmdoc.github.io/node-npmdoc-favicons-webpack-plugin/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-favicons-webpack-plugin_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-favicons-webpack-plugin/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-favicons-webpack-plugin/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-favicons-webpack-plugin/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Jan Nicklas",
        "email": "j.nicklas@me.com",
        "url": "https://github.com/jantimon"
    },
    "bugs": {
        "url": "https://github.com/jantimon/favicons-webpack-plugin/issues"
    },
    "dependencies": {
        "favicons": "^4.7.1",
        "loader-utils": "^0.2.14",
        "lodash": "^4.11.1",
        "webpack": "^1.13.0"
    },
    "description": "Let webpack generate all your favicons and icons for you",
    "devDependencies": {
        "ava": "^0.14.0",
        "babel-eslint": "^6.0.2",
        "denodeify": "^1.2.1",
        "dir-compare": "^1.0.1",
        "express": "^4.13.4",
        "html-webpack-plugin": "^2.16.0",
        "memory-fs": "^0.3.0",
        "mkdirp": "^0.5.1",
        "rimraf": "^2.5.2",
        "semistandard": "^7.0.5",
        "webpack": "^1.13.0",
        "webpack-dev-middleware": "^1.6.1"
    },
    "directories": {},
    "dist": {
        "shasum": "253a46a4f93d137d1096762877f8a8ef12e28648",
        "tarball": "https://registry.npmjs.org/favicons-webpack-plugin/-/favicons-webpack-plugin-0.0.7.tgz"
    },
    "files": [
        "index.js",
        "lib/"
    ],
    "gitHead": "ad68acdb8302df73579c39c12db43e2f2b0f9c31",
    "homepage": "https://github.com/jantimon/favicons-webpack-plugin",
    "keywords": [
        "webpack",
        "plugin",
        "html-webpack-plugin",
        "favicon",
        "icon"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "jantimon",
            "email": "j.nicklas@me.com"
        }
    ],
    "name": "favicons-webpack-plugin",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/jantimon/favicons-webpack-plugin.git"
    },
    "scripts": {},
    "semistandard": {
        "parser": "babel-eslint"
    },
    "version": "0.0.7"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module favicons-webpack-plugin](#apidoc.module.favicons-webpack-plugin)
1.  object <span class="apidocSignatureSpan">favicons-webpack-plugin.</span>cache
1.  object <span class="apidocSignatureSpan">favicons-webpack-plugin.</span>compiler

#### [module favicons-webpack-plugin.cache](#apidoc.module.favicons-webpack-plugin.cache)
1.  [function <span class="apidocSignatureSpan">favicons-webpack-plugin.cache.</span>emitCacheInformationFile (loader, query, cacheFile, fileHash, iconResult)](#apidoc.element.favicons-webpack-plugin.cache.emitCacheInformationFile)
1.  [function <span class="apidocSignatureSpan">favicons-webpack-plugin.cache.</span>loadIconsFromDiskCache (loader, query, cacheFile, fileHash, callback)](#apidoc.element.favicons-webpack-plugin.cache.loadIconsFromDiskCache)

#### [module favicons-webpack-plugin.compiler](#apidoc.module.favicons-webpack-plugin.compiler)
1.  [function <span class="apidocSignatureSpan">favicons-webpack-plugin.compiler.</span>compileTemplate (options, context, compilation)](#apidoc.element.favicons-webpack-plugin.compiler.compileTemplate)



# <a name="apidoc.module.favicons-webpack-plugin"></a>[module favicons-webpack-plugin](#apidoc.module.favicons-webpack-plugin)



# <a name="apidoc.module.favicons-webpack-plugin.cache"></a>[module favicons-webpack-plugin.cache](#apidoc.module.favicons-webpack-plugin.cache)

#### <a name="apidoc.element.favicons-webpack-plugin.cache.emitCacheInformationFile"></a>[function <span class="apidocSignatureSpan">favicons-webpack-plugin.cache.</span>emitCacheInformationFile (loader, query, cacheFile, fileHash, iconResult)](#apidoc.element.favicons-webpack-plugin.cache.emitCacheInformationFile)
- description and source-code
```javascript
function emitCacheInformationFile(loader, query, cacheFile, fileHash, iconResult) {
  if (!query.persistentCache) {
    return;
  }
  loader.emitFile(cacheFile, JSON.stringify({
    hash: fileHash,
    version: pluginVersion,
    optionHash: generateHashForOptions(query),
    result: iconResult
  }));
}
```
- example usage
```shell
...
  if (err) return callback(err);
  if (cachedResult) {
    return callback(null, 'module.exports = ' + JSON.stringify(cachedResult));
  }
  // Generate icons
  generateIcons(self, content, pathPrefix, query, function (err, iconResult) {
    if (err) return callback(err);
    faviconPersitenceCache.emitCacheInformationFile(self, query, cacheFile, fileHash, iconResult);
    callback(null, 'module.exports = ' + JSON.stringify(iconResult));
  });
});
};

function getPublicPath (compilation) {
var publicPath = compilation.outputOptions.publicPath || '';
...
```

#### <a name="apidoc.element.favicons-webpack-plugin.cache.loadIconsFromDiskCache"></a>[function <span class="apidocSignatureSpan">favicons-webpack-plugin.cache.</span>loadIconsFromDiskCache (loader, query, cacheFile, fileHash, callback)](#apidoc.element.favicons-webpack-plugin.cache.loadIconsFromDiskCache)
- description and source-code
```javascript
function loadIconsFromDiskCache(loader, query, cacheFile, fileHash, callback) {
  // Stop if cache is disabled
  if (!query.persistentCache) return callback(null);
  var resolvedCacheFile = path.resolve(__dirname, loader._compiler.parentCompilation.compiler.outputPath, cacheFile);

  fs.exists(resolvedCacheFile, function (exists) {
    if (!exists) return callback(null);
    fs.readFile(resolvedCacheFile, function (err, content) {
      if (err) return callback(err);
      var cache;
      try {
        cache = JSON.parse(content);
        // Bail out if the file or the option changed
        if (!isCacheValid(cache, fileHash, query)) {
          return callback(null);
        }
      } catch (e) {
        return callback(e);
      }
      callback(null, cache.result);
    });
  });
}
```
- example usage
```shell
...
});
var fileHash = loaderUtils.interpolateName(self, '[hash]', {
  context: query.context || this.options.context,
  content: content,
  regExp: query.regExp
});
var cacheFile = pathPrefix + '.cache';
faviconPersitenceCache.loadIconsFromDiskCache(self, query, cacheFile, fileHash, function (err, cachedResult) {
  if (err) return callback(err);
  if (cachedResult) {
    return callback(null, 'module.exports = ' + JSON.stringify(cachedResult));
  }
  // Generate icons
  generateIcons(self, content, pathPrefix, query, function (err, iconResult) {
    if (err) return callback(err);
...
```



# <a name="apidoc.module.favicons-webpack-plugin.compiler"></a>[module favicons-webpack-plugin.compiler](#apidoc.module.favicons-webpack-plugin.compiler)

#### <a name="apidoc.element.favicons-webpack-plugin.compiler.compileTemplate"></a>[function <span class="apidocSignatureSpan">favicons-webpack-plugin.compiler.</span>compileTemplate (options, context, compilation)](#apidoc.element.favicons-webpack-plugin.compiler.compileTemplate)
- description and source-code
```javascript
function compileTemplate(options, context, compilation) {
  // The entry file is just an empty helper as the dynamic template
  // require is added in "loader.js"
  var outputOptions = {
    filename: options.statsFilename,
    publicPath: compilation.outputOptions.publicPath
  };
  // Create an additional child compiler which takes the template
  // and turns it into an Node.JS html factory.
  // This allows us to use loaders during the compilation
  var compilerName = getCompilerName(context, outputOptions.filename);
  var childCompiler = compilation.createChildCompiler(compilerName, outputOptions);
  childCompiler.context = context;
  childCompiler.apply(
    new SingleEntryPlugin(context, '!!' + require.resolve('./favicons.js') + '?' +
      JSON.stringify({
        outputFilePrefix: options.prefix,
        icons: options.icons,
        background: options.background,
        persistentCache: options.persistentCache,
        appName: options.title
      }) + '!' + options.logo)
  );

  // Fix for "Uncaught TypeError: __webpack_require__(...) is not a function"
  // Hot module replacement requires that every child compiler has its own
  // cache. @see https://github.com/ampedandwired/html-webpack-plugin/pull/179
  childCompiler.plugin('compilation', function (compilation) {
    if (compilation.cache) {
      if (!compilation.cache[compilerName]) {
        compilation.cache[compilerName] = {};
      }
      compilation.cache = compilation.cache[compilerName];
    }
    compilation.plugin('optimize-chunk-assets', function (chunks, callback) {
      if (!chunks[0]) {
        return callback(compilation.errors[0] || 'Favicons generation failed');
      }
      var resultFile = chunks[0].files[0];
      var resultCode = compilation.assets[resultFile].source();
      var resultJson;
      try {
<span class="apidocCodeCommentSpan">        /*eslint no-eval:0 */
</span>        var result = eval(resultCode);
        resultJson = JSON.stringify(result);
      } catch (e) {
        return callback(e);
      }
      compilation.assets[resultFile] = {
        source: function () {
          return resultJson;
        },
        size: function () {
          return resultJson.length;
        }
      };
      callback(null);
    });
  });

  // Compile and return a promise
  return new Promise(function (resolve, reject) {
    childCompiler.runAsChild(function (err, entries, childCompilation) {
      if (err) {
        return reject(err);
      }
      // Replace [hash] placeholders in filename
      var outputName = compilation.mainTemplate.applyPluginsWaterfall('asset-path', outputOptions.filename, {
        hash: childCompilation.hash,
        chunk: entries[0]
      });
      // Resolve / reject the promise
      if (childCompilation && childCompilation.errors && childCompilation.errors.length) {
        var errorDetails = childCompilation.errors.map(function (error) {
          return error.message + (error.error ? ':\n' + error.error : '');
        }).join('\n');
        reject(new Error('Child compilation failed:\n' + errorDetails));
      } else if (err) {
        reject(err);
      } else {
        resolve({
          outputName: outputName,
          stats: JSON.parse(childCompilation.assets[outputName].source())
        });
      }
    });
  });
}
```
- example usage
```shell
...
if (!self.options.title) {
  self.options.title = guessAppName(compiler.context);
}

// Generate the favicons
var compilationResult;
compiler.plugin('make', function (compilation, callback) {
  childCompiler.compileTemplate(self.options, compiler.context, compilation)
    .then(function (result) {
      compilationResult = result;
      callback();
    })
    .catch(callback);
});
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
