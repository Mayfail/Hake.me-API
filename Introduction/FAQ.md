# FAQ

## How do I add a whitelisted hostname?

Some scripts may want to make requests to third party websites while you play (for looking up statistics or querying some information based on your match). For your saftey all such requests will fail by default unless you explicitly whitelist the host. To do so, simply create a `whitelisted_hosts.txt`​ file in the folder where you keep `client.exe`​. Then add the hostname to it, one per line (IP addresses can be used as well).

### Example `whitelisted_hosts.txt`​

```
google.com
hake.me
localhost
translate-alfred.herokuapp.com
statistics.kostya12rus.ru
101.200.189.65
```
