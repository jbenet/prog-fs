# prog-fs - program filesystems

This repo demonstrates a cute idea: using ipfs and interpreters to make "filesystems" whose files are the result of executing programs.

Beyond the cute idea, this is a way to explore filesystems which store traditional files or databases in code representations, with low [kolmogorov complexity](https://en.wikipedia.org/wiki/Kolmogorov_complexity).

Examples:
- [`shfs` - shell-fs](shfs/)
- [`jsfs` - javascript-fs](jsfs/)



#### TODO: add a FUSE interface

so they feel like proper filesystems:

```
> cat /jsfs/QmY2mfGU1Agr9gUDgM1Q8BQxTmqp2vBD4CQ8GLY8o8x1Mi/date
Wed Dec 02 2015 08:40:55 GMT-0800 (PST)

> cat /jsfs/QmY2mfGU1Agr9gUDgM1Q8BQxTmqp2vBD4CQ8GLY8o8x1Mi/date
Wed Dec 02 2015 08:40:56 GMT-0800 (PST)
```
