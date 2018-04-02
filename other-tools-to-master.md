# Other Tools to Master

Here are a list of tools that appear in the lab exercises that are not explictly listed in the GIAC GSE exam objectives (https://www.giac.org/certification/security-expert-gse).

## base64

```
base64 -d [file containing base64]
```

## xxd

xxd is used to make a hexdump or to revert hexdumps to something readable.
The following example reverts (-r) hex into something readable. The "-p" specifies postscript, aka plain hexdump style.

```
xxd -r -p
```



