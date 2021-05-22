# Novaposhta API

First, create or find existing api key

https://new.novaposhta.ua/dashboard/settings/developers

Use it as goes:

```
$ ./novaposhta [--api-key=XXXXXX]
```

See below for different methods to store API key securely.

# Options: 

- --format=json - (tabular is default)

- --raw - (to output all fields in requested format. By default, only human-readable subset is rendered)

- --api-key - actually not required if token had been stored in file as described below

You can store API key to pass(1). KeepassXC backend may also be implemented, if somebody interested in. Then specify path to stored token in argument:


```
$ ./novaposhta --api-key=pass://private/mgr/novaposhta 
```

Or write token to file In fact $HOME/.novaposhta-cli is hardcoded default value to use if no
argument has been specified.

```
$ ./novaposhta --api-key=file://$HOME/.novaposhta-cli
```

File in turn can also contain either plain-text token or link to pass. Example:

```
$ cat ~/.novaposhta-cli
pass://private/mgr/novaposhta
```

So finally in such setup we can call the script without any argument:

```
$ novaposhta

Number | Status                                                     | CargoDescription            |   Money | From
```

# FILTERING

By default, all active receipts are shown. I.e. no filtering applied client side except of server-side visibility. With filtering options one can limit output to only given states:

- --ready : delivered to post office

- --paid : payment transferred to sender

- --delivered : delivered to recipient (me)

Any combination of those is pretty valid:

```
$ novaposhta --paid --delivered
$ novaposhta --delivered --ready
```

I would like to add more states, like 'on the way' (and display estimated schedule), etc. etc. Unfortunately I have no data to validate against. If somebody can provide debug json dumps (see below) with their receipts of different states it will help a lot. You should, of course, anonymize embedded data as far as needed.

# HACKING

There is no good in hitting NP API frequently but it may happen during code development and debug. It's better to use static data in such case. Debug dump can be saved by:

```
$ npcli --format=json --raw > ~/np-debug.json
```

Then use it instead of calling API by specifying --debug-file option:

```
$ npcli --debug-file ~/np-debug.json --delivered
```
