# jsfs - javascript filesystem

ipfs-based filesystem whose files are the result of executing javascript programs.

**Note:** of course, `jsfs` could be trivially implemented on top of `shfs` if all files include the `#!/usr/bin/env node` line. :)

## Example

```sh
# say we have a javascript file like this
> cat examples/date.js
console.log(new Date())

# we add it to the filesystem
> jsfs add examples/date.js
added QmaaRZQ2xBUnVkqt3HWAChngdkyHMQxnQf4j9fdZpkxGr1 date.sh

# when we output it, it executes
> jsfs cat QmY2mfGU1Agr9gUDgM1Q8BQxTmqp2vBD4CQ8GLY8o8x1Mi/date.js
Wed Dec 02 2015 08:40:55 GMT-0800 (PST)

# when we output it again, it executes again
> jsfs cat QmY2mfGU1Agr9gUDgM1Q8BQxTmqp2vBD4CQ8GLY8o8x1Mi/date.js
Wed Dec 02 2015 08:40:56 GMT-0800 (PST)
```

## Try it out!

- Step 1. make sure you have IPFS installed and running: https://ipfs.io/docs/install
- Step 2. get `jsfs`

  ```sh
  git clone https://github.com/jbenet/prog-fs
  cd prog-fs/jsfs
  ```

- Step 3. run examples

  ```sh
  > ./jsfs add -r examples
  added QmaaRZQ2xBUnVkqt3HWAChngdkyHMQxnQf4j9fdZpkxGr1 examples/date.js
  added QmNfeT8e8JkvgWE9DSp7Y5FBKpeynavqcN29LcgvVMXgLd examples/random.js
  added QmY2mfGU1Agr9gUDgM1Q8BQxTmqp2vBD4CQ8GLY8o8x1Mi examples

  > ./jsfs cat QmY2mfGU1Agr9gUDgM1Q8BQxTmqp2vBD4CQ8GLY8o8x1Mi/date.js
  Wed Dec 02 2015 08:40:55 GMT-0800 (PST)

  > ./jsfs cat QmY2mfGU1Agr9gUDgM1Q8BQxTmqp2vBD4CQ8GLY8o8x1Mi/date.js
  Wed Dec 02 2015 08:40:56 GMT-0800 (PST)

  > ./jsfs cat QmY2mfGU1Agr9gUDgM1Q8BQxTmqp2vBD4CQ8GLY8o8x1Mi/random.js
  0.82436887267977

  > ./jsfs cat QmY2mfGU1Agr9gUDgM1Q8BQxTmqp2vBD4CQ8GLY8o8x1Mi/random.js
  0.3454080908559263
  ```
