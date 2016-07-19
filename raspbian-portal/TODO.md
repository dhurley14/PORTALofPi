## Securing Raspbian

1. `sudo apt install unattended-upgrades`
2. find `Unattended-Upgrade::Origins-Pattern` and replace it with the following 
```
Unattended-Upgrade::Origins-Pattern {
        // Archive or Suite based matching:
        // Note that this will silently match a different release after
        // migration to the specified archive (e.g. testing becomes the
        // new stable).
//      "o=Raspbian,a=stable";
//      "o=Raspbian,a=stable-updates";
//      "o=Raspbian,a=proposed-updates";
        "origin=Raspbian,archive=stable,label=Raspbian-Security";
};
```
3. sudo nano /etc/apt/apt.conf.d/20auto-upgrades
```
 APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";
```
4. follow the rest of this https://www.linode.com/docs/security/securing-your-server/

  a. create no-priv user used to update `/etc/wpa_supplicant/wpa_supplicant.conf`
     if possible..
