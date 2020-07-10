# node-occ

OpenCascade nodejs extension for solid modeling.

This nodejs extension provides _solid construction_ to nodejs.
It provides a simple yet powerful javascript api to construct 3D geometry models.

This project comes with a set of V8 wrappers around OpenCascade API and a sample web application.

[![Build Status](https://travis-ci.org/OpenWebCAD/node-occ.png?branch=master)](https://travis-ci.org/OpenWebCAD/node-occ)
[![Build status](https://ci.appveyor.com/api/projects/status/s5eaux89v2c0wmu4?svg=true)](https://ci.appveyor.com/project/erossignon/node-occ-6ktv4)

### quick example

```javascript
var occ = require("node-occ").occ;

// construct a box
var box = occ.makeBox([0, 0, 0], [100, 100, 50]);

// construct a cylinder
var cyl = occ.makeCylinder([50, 50, -10], [50, 50, 60], 40);

// cut the box with cylinder
box = occ.cut(box, cyl);

// save result to a STEP file
occ.writeSTEP("somefile.step", box);
```

### video

<a href="http://www.youtube.com/watch?feature=player_embedded&v=swUPSa2zyrY" target="_blank"><img src="http://img.youtube.com/vi/swUPSa2zyrY/0.jpg" 
alt="node occ" width="240" height="180" border="10" /></a>

### list of features

-   creation of basic shapes ( box, cylinder , cone , torus )
-   boolean operation ( fuse , common , cut )
-   features ( draftAngle)
-   solid properties ( faces, edges, vertices, area , volume )
-   import export ( STEP BREP )

## installing node-occ from npm

```
$npm install node-occ
```

## building node-occ from source : prerequisites

### on Ubuntu

(use nodejs 12.0)

```bash
# installing nodejs and gyp utility to build extensions
sudo apt-get install nodejs npm
sudo npm install node-pre-gyp -g
sudo npm install mocha -g

#installing cmake
sudo apt-get install cmake cmake-curses-gui g++ build-essential libtbb2

# ------------------------------------
git clone --recursive https://github.com/erossignon/node-occ.git
cd node-occ
export OCCT_PACKAGE=occt-7.2.0
export LD_LIBRARY_PATH=`pwd`/${OCCT_PACKAGE}/lib:$LD_LIBRARY_PATH
# Download occt from https://github.com/OpenWebCAD/occt_builder/releases/download/7.2.0/occt-7.2.0-linux.tgz
# Extract into occt-7.2.0
npm install --build-from-source
make test
```

### sample web application

[node-occ-sample](https://github.com/erossignon/node-occ-sample): sample nodejs/express REST API server to build solid , based on threejs

```bash
git clone https://github.com/OpenWebCAD/node-occ-sample.git
cd node-occ-sample
# Install dependencies
npm install

# Install node-occ mannually
cd node_modules
git clone --recursive https://github.com/erossignon/node-occ.git
cd node-occ
export OCCT_PACKAGE=occt-7.2.0
export LD_LIBRARY_PATH=`pwd`/${OCCT_PACKAGE}/lib:$LD_LIBRARY_PATH
# Download occt from https://github.com/OpenWebCAD/occt_builder/releases/download/7.2.0/occt-7.2.0-linux.tgz
# Extract into occt-7.2.0
npm install --build-from-source
make test

# Run
npm start
```

## dependencies:

-   threejs : https://github.com/mrdoob/three.js

## acknowledgement:

-   OpenCascade : http://www.opencascade.org
-   occmodel : https://github.com/tenko/occmodel
-   ShapeSmith : https://github.com/bjnortier/shapesmith

## MIT License

Copyright © 2012-2019 E. Rossignon

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
