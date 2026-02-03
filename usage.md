# Adding a new host:

Get the age-formatted public host key:
```
ssh-keyscan <hostname> | ssh-to-age
```

Add that to `.sops.yaml` as appropriate.

Run `sops updatekeys` on all relevant files.

# Add SOPS master key to gpg

The master key is stored in Bitwarden, which mangles the ascii armoring
somewhat. When unmangled and put into a file `secret.key`, do `gpg
--import-secret-keys secret.key` as root.
