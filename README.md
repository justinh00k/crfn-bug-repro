I am using esm to use modules in gatsby-node.js. So my gatsby-node.js looks like this:

```
const requireEsm = require("esm")(module)
module.exports = requireEsm("./gatsby-node.esm.js")
```

In gatsby-node.esm.js, this line causes an error:
`import { createRemoteFileNode } from "gatsby-source-filesystem"`

```
Error: {site}/node_modules/gatsby-source-filesystem/create-remote-file-node.js:1
Error: Cannot find module 'gatsby-core-utils/fetch-remote-file'
```

I can fix the problem by modifying this line on gatsby-source-filesystem.js
`const { fetchRemoteFile } = require(`gatsby-core-utils/fetch-remote-file`);`
to
`const { fetchRemoteFile } = require(`gatsby-core-utils`);`

-
