# React Jodit WYSIWYG Editor

[![npm](https://img.shields.io/npm/v/jodit-react.svg)](https://www.npmjs.com/package/jodit-react)
[![npm](https://img.shields.io/npm/dm/jodit-react.svg)](https://www.npmjs.com/package/jodit-react)
[![npm](https://img.shields.io/npm/l/jodit-react.svg)](https://www.npmjs.com/package/jodit-react)

**jodit-react** is a react wrapper for [Jodit](https://xdsoft.net/jodit/) WYSIWYG Editor.

## Why do we need custom build?
We need to use **typescript** `v3` **jodit** version in the **venue-edit-client** project.

**jodit v3.4.23** is the last version which is using **typescript** version 3.

**jodit-react v1.0.59** requires **jodit v3.4.23** as dependency and it looks like we can use this version in the **venue-edit-client** project.

But in **jodit-react** project, **jodit** is linked with `^3.4.23` and the latest version of **jodit v3**(which is using **typescript v4**) is installed.

It makes us not to use the official version of **jodit-react**.

## How to publish a new version?
Switch to a version tag to use.

In the **package.json** file, do the following.
* Remove caret(^) character in **jodit** dependency.
* Rename the package to `@seeticketsus/jodit-react`.
```
{
  "name": "@seeticketsus/jodit-react",
  ...
  "dependencies": {
    "jodit": "3.5.4"
  },
  ...
}
```


Run the follwing commands to publish a new version.
```
$ npm install
$ npm run build
$ npm login # login with your seetickets email
$ npm publish
```

## Installation

```bash
npm install jodit-react --save
```

## Update editor version
```bash
npm update jodit-react
```

## Run demo
```bash
npm install --dev
npm run demo
```

and open
```
http://localhost:4000/
```

## Usage

### 1. Require and use Jodit-react component inside your application.

```jsx
import React, {useState, useRef} from 'react';
import JoditEditor from "jodit-react";

const Example = ({}) => {
	const editor = useRef(null)
	const [content, setContent] = useState('')

	const config = {
		readonly: false // all options from https://xdsoft.net/jodit/doc/
	}

	return (
            <JoditEditor
            	ref={editor}
                value={content}
                config={config}
		tabIndex={1} // tabIndex of textarea
		onBlur={newContent => setContent(newContent)} // preferred to use only this option to update the content for performance reasons
                onChange={newContent => {}}
            />
        );
}
```


License
-----
This package is available under `MIT` License.
