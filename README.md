# novaposhta

First, create or found existing api key

https://new.novaposhta.ua/dashboard/settings/developers


$ ./novaposhta --api-key=XXXXXX

Options: 

--format=json (tabular is default)

--raw (to output all fields in requested format. By default, only human-readable subset is rendered)

Optinally, you can store API key in pass(1) and specify path to stored token as:

$ ./novaposhta --api-key=pass://private/mgr/novaposhta 

KeepassXC backend may also be implemented, if somebody interested in.
