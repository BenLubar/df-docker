# Dwarf Fortress in Docker

Important note: if the host is running an OS with seccomp, such as Ubuntu 15.10 or later, you will need to add `--security-opt=seccomp=unconfined` or alter the [default Docker profile](https://github.com/docker/docker/blob/master/profiles/seccomp/default.json) to allow `personality(ADDR_NO_RANDOMIZE)` (0x0040000) to your dfhack container's run command.
