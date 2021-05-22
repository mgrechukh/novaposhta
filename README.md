# novaposhta

First, create or found existing api key

https://new.novaposhta.ua/dashboard/settings/developers


```
$ ./novaposhta [--api-key=XXXXXX]
```

Options: 

--format=json - (tabular is default)

--raw - (to output all fields in requested format. By default, only human-readable subset is rendered)

--api-key - is not required if token had been stored in file as described below.

You can store API key to pass(1). KeepassXC backend may also be implemented, if somebody interested in.

Then specify path to stored token in argument:


```
$ ./novaposhta --api-key=pass://private/mgr/novaposhta 
```

Or write it to file:

```
$ ./novaposhta --api-key=file://$HOME/.novaposhta-cli
```

In fact $HOME/.novaposhta-cli is hardcoded default value to use if no
argument has been specified.

File can in turn also contain either plain-txt token or link to pass. Example:

```
$ cat ~/.novaposhta-cli
pass://private/mgr/novaposhta
```

So finally in such setup we can call the script without any argument:

```
$ novaposhta

Number | Status                                                     | CargoDescription            |   Money | From
```

