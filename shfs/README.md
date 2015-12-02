# shfs - shell filesystem

ipfs-based filesystem whose files are the result of executing shell programs.

## Example

```sh
# say we have a shell script which runs date
> cat examples/date.sh
#!/bin/sh
date

# we add it to the filesystem
> shfs add examples/date.sh
added QmSBwWeRh7LcKBqvrCzpbgBpSYYPLNFBP7BFKF9mczFqir date.sh

# when we output it, it executes
> shfs cat QmSBwWeRh7LcKBqvrCzpbgBpSYYPLNFBP7BFKF9mczFqir
Wed Dec  2 08:31:37 PST 2015

# when we output it again, it executes again
> shfs cat QmSBwWeRh7LcKBqvrCzpbgBpSYYPLNFBP7BFKF9mczFqir
Wed Dec  2 08:31:39 PST 2015
```

## Try it out!

- Step 1. make sure you have IPFS installed and running: https://ipfs.io/docs/install
- Step 2. get `shfs`

  ```sh
  git clone https://github.com/jbenet/prog-fs
  cd prog-fs/shfs
  ```

- Step 3. run examples

  ```sh
  > ./shfs add -r examples
  added QmSBwWeRh7LcKBqvrCzpbgBpSYYPLNFBP7BFKF9mczFqir examples/date.sh
  added QmQLcbitV8jsVsTmbs2jAACyQBcnuBiVwnzeLqFh9tFtC1 examples/rand.sh
  added QmVqehjULfUgEmAQaP4dN8T4sJ2QkCnoSbh7XW1hnQW9cp examples

  > ./shfs cat QmVqehjULfUgEmAQaP4dN8T4sJ2QkCnoSbh7XW1hnQW9cp/date.sh
  Wed Dec  2 08:37:09 PST 2015

  > ./shfs cat QmVqehjULfUgEmAQaP4dN8T4sJ2QkCnoSbh7XW1hnQW9cp/rand.sh | base64 | head -c 100
  lBZCzCqu8p97EmoXW4tO6ShfVqABb68Pm1pvbbsiZJ5U6BmiK4Ze9BC3FslH/Ry4W2UwympMR87+vhaJdAhpiAC49gSF7F1K3Dtr

  > ./shfs cat QmVqehjULfUgEmAQaP4dN8T4sJ2QkCnoSbh7XW1hnQW9cp/rand.sh | base64 | head -c 100
  fDViImon5VgjH0XsgvMB+CY7TWqNxjPNvKCg+uNlkRULik7o72xmd3v9F+tJYInxFWyVKMDwXudpjyIL6ixCHlJwGlhNMfeLbM1k
  ```
