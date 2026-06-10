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
--import secret.key`.


# Generating nix-serve keys

See [wiki/Binary Cache](https://nixos.wiki/wiki/Binary_Cache).

``` 
nix-store --generate-binary-cache-key binarycache.example.com cache-priv-key.pem cache-pub-key.pem
``` 

# Generating new age keys

Use `age-keygen`. See [sops-nix](https://github.com/Mic92/sops-nix#usage-example).

```
$ mkdir -p ~/.config/sops/age
$ age-keygen -o ~/.config/sops/age/keys.txt
```

On MacOS, `keys.txt` lives in `~/Library/Application
Support/sops/age/keys.txt` (Unless `$XDG_CONFIG_HOME` is set). See [SOPS:
Secrets OPerations / Encrypting using age](https://getsops.io/docs/).
