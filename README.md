# Saltstack Encrypt Strings
Implement an encryption / decryption scheme for storing and accessing sensitive data (e.g. passwords). The saltmaster stores the encrypted strings as pillars. Minions must be assigned pillars to access the data.

# saltmaster-onetimesetup
Generates the key/files used to encrypt.

# saltmaster-encryptstring
Generates the encrypted string in saltstack's format

# pillar-top-example.txt
Example pillar.sls for salt master

# managed file example
```
# state file to expose a string, note template: jinja
/tmp/expose-string.txt:
  file.managed:
    - source:
      - salt://expose-string/expose-string.txt
    - user: root
    - group: root
    - mode: 600
    - attrs: i
    - template: jinja
    - backup: minion

# expose-string.txt
{{ salt['pillar.get']('expose-string') }}
```
