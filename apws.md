Links: [[PROJECTS]]

--- 
MANAGER (general -> specific) 

| CONNECTOR (live) | L1 (ACTION // ACCESS) | CACHER (historical) |
| -------- | -------- | -------- |
| L2 (PATH)     | RESOURCE     | (ACCESS)     |
| Endpoint ->  | JSSResponse | <- Datapath  |
| L3 (NOUN)  | L3 (NOUN)  | (ACCESS)  |
|  | ^ JSSAttribute v |  |



- "resource_key" vs "endpointkey"
- Get ID back from "x_id" request
- fxn browser open api documentation https://www/jamf.com/developers/apis/classic/reference/#/{endpoint}
	- -> auto docs via YAML parsing

- extension_attributes
- group_memberships as bool
- 
- create **listener** to recieve event(s) and interact with other applications or services [Translator']
- EndUser "manipulatable" Config Profile triggers
- 



### JSSEndpoint (L2) 
##### endpoint class to handle for all endpoint (/resource string parsing)
- id_types -> sub_id (e.g. ../patchsoftware/id/{id}/ )
	- or -> "range_id"
	- id_name, id_sn, ...
- subset_basic
- id_directory
- sub_infos (<-> id.json JSSObject)


### JSSAttribute (L3)


### JSSObject (L3)
- dict.get() handle for as_ XML
- NamedTuple access object interface
	- -> list of keys -> flat objects
- preconfig capture keys -> load 
	-> drill for key_finder puts (self['recent'] = [])


### JSSResponse (L2)
- handle for cache pulled objects (.get() -> .where())
	- & a .match() equivalent
- .get("name") -> .replace('name', 'new-name-here')
- 


### JSSContainer (L3)
- .get("name**s**")


### JSSCONN (L1)
- .match(,exact=True) -> fix "_exactor" functionality ; further handle for empty return
- .get(\*\*kwargs -> id_types)
- configparser.CofigParser (-> auth/data class?)
- ._auth -> /JSSCheckConnection


### DATAPATH (L2) DATADIFFER
- (or req_date @property handle on JSSCACHE)
- handle for datetime dir parameter grabs (0->index recent -> past)


### JSSCACHE (L1)
- .get() -> .load() concurrently
- XML cache (for PUT/POST templating)
- to_csv
- cache_('computers') -> cache_computers (META)


### Resource (L1)

