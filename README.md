# Dwarf Fortress in Docker

Important note: if the host is running an OS with seccomp, such as Ubuntu 15.10 or later, you will need to add `--security-opt=seccomp=unconfined` or alter the [default Docker profile](https://github.com/docker/docker/blob/master/profiles/seccomp/default.json) to allow `personality(ADDR_NO_RANDOMIZE)` (0x0040000) to your dfhack container's run command.

```
{
	"names": [
		"personality"
	],
	"action": "SCMP_ACT_ALLOW",
	"args": [
		{
			"index": 0,
			"value": 262144,
			"valueTwo": 0,
			"op": "SCMP_CMP_EQ"
		}
	],
	"comment": "[ADDR_NO_RANDOMIZE] Allow disabling ASLR (Address Space Layout Randomization), which DFHack needs in order to run.",
	"includes": {},
	"excludes": {}
},
```
