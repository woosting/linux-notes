# Auto start (system.d)

Systemd is a suite of system management daemons, libraries, and utilities designed as a central management and configuration platform for the Linux computer operating system. It also offers users the ability to manage services under the user’s control with a per-user systemd instance, enabling users to start, stop, enable, and disable their own units. Service files for systemd are provided by Syncthing and can be found in [etc/linux-systemd][2].

<!--
    You have two primary options: You can set up Syncthing as a **system service**, or a **user service**.

    - Running Syncthing as a **system service** ensures that Syncthing is run at startup even if the Syncthing user has no active session. Since the system service keeps Syncthing running even without an active user session, it is intended to be used on a _server_.

    - Running Syncthing as a **user service** ensures that Syncthing only starts after the user has logged into the system (e.g., via the graphical login screen, or ssh). Thus, the user service is intended to be used on a _(multiuser) desktop computer_. It avoids unnecessarily running Syncthing instances.
-->

## Start as System service (upon boot)

1. Create a user who's user-space the service should run in (if not present already):

	```
	# adduser <username>
	```
2. Follow instructions on screen.

2. Copy the service file into the [load path of the system instance][3] (as root):

    - When installed via _Apt_ on Debian 8:

		```
		# cp /lib/systemd/system/syncthing@.service /etc/systemd/system
		```

    - When installed via _wget, curl or other manual download_:

		```
		# cp <installdir>/etc/linux-systemd/system/syncthing@.service /etc/systemd/system
		```

	> NOTE: Several distros (among which Arch linux) ship the needed service files with the Syncthing package. If your distro provides a systemd service file for Syncthing, you can skip this step!

3. Enable the service:

	```
	# systemctl enable syncthing@<user>.service
	```

4. Start the service:

	```
	# systemctl start syncthing@<user>.service
	```

## Troubleshooting

### Check service status

Check if Syncthing runs properly:

```
$ systemctl status -l syncthing@<user>.service
```

### Investigate log-file (journal)

Display the logs for the system service:

```
$ journalctl -e -u syncthing@<user>.service
```

> `-e` jump to the end, so that you see the most recent logs

> NOTE: Running Syncthing as a service expects the executable to be at: */usr/bin/syncthing* (on Debian deratives), so (at least) make a symbolic link to the executable from that location should Syncthing fail to start with the journal stating it can not find the executable:
> ```
> ln -s <install-dir>/syncthing /usr/bin/syncthing
> ```


## Permissions

If _'Ignore Permissions'_ is set in the Syncthing client’s folder settings, then the line `UMask=0002` (or any other _umask setting <http://www.tech-faq.com/umask.html>_ you like) also needs to be set in the `[Service]` section of the `syncthing@.service file`.


## Appendix: Unit load paths

Table 1. Load path when running in system mode (--system):

|Path|Description|
|----|-----------|
|/etc/systemd/system|Local configuration|
|/run/systemd/system|Runtime units|
|/usr/lib/systemd/system|Units of installed packages|

> NOTE: `/etc/systemd/system` is known to have been successfully used in a Debian Jessie LXC ARM7.1 container!


<!--
## Start as User service (upon login)

1. Create the user who should run the service, or choose an existing one. _Probably this will be your own user account._
2. Copy the `Syncthing/etc/user/syncthing.service` file into the  [load path of the user instance][3] (also see Table 2. in the appendix below). To do this without root privileges you can just use this folder under your home directory: `~/.config/systemd/user/`.

    ***Note:** Several distros (among which Arch linux) ship the needed service files with the Syncthing package. If your distro provides a systemd service file for Syncthing, you can skip step 2 when setting up either the system service or the user service*

3. Issue: `systemctl --user enable syncthing.service` to enable the service:
  ```shell
  systemctl --user enable syncthing.service
  ```
4. Issue: `systemctl --user enable syncthing.service` to start the service:
  ```shell
  systemctl --user start syncthing.service
```

### Check the (user) service status

- Issue: `systemctl --user status syncthing.service` to check if Syncthing runs properly:
```shell
systemctl --user status syncthing.service
```

> **Note:** Running Syncthing as a service expects the executable to be at: **/usr/bin/syncthing**, so (at least) make a symbolic link to the executable from that location should it fail to start and the journal states it can not find the executable at that location: `ln -s /Syncthing/syncthing (on Debian deratives)`.


### Logging

- Issue: `journalctl -e --user-unit=syncthing.service` to see the logs for the user service, with `-e` telling the pager to jump to the very end, so that you see the most recent logs:
  ```shell
  journalctl -e --user-unit=syncthing.service
  ```

Table 2. Load path when running in user mode (--user).

|Path|Description|
|----|-----------|
|$XDG_CONFIG_HOME/systemd/user|User configuration (only used when $XDG_CONFIG_HOME is set)|
|$HOME/.config/systemd/user|User configuration (only used when $XDG_CONFIG_HOME is not set)|
|/etc/systemd/user|Local configuration|
|$XDG_RUNTIME_DIR/systemd/user|Runtime units (only used when $XDG_RUNTIME_DIR is set)|
|/run/systemd/user|Runtime units|
|$XDG_DATA_HOME/systemd/user|Units of packages that have been installed in the home directory (only used when $XDG_DATA_HOME is set)|
|$HOME/.local/share/systemd/user|Units of packages that have been installed in the home directory (only used when $XDG_DATA_HOME is not set)|
|/usr/lib/systemd/user|Units of packages that have been installed system-wide|
-->

## References

> Adapted from: Official Syncthing documentation
> [Starting Syncthing Automatically][1]


<!-- REFERENCES -->
[1]:https://docs.syncthing.net/users/autostart.html?highlight=starting#using-systemd
[2]:https://github.com/syncthing/syncthing/tree/master/etc/linux-systemd
[3]:https://www.freedesktop.org/software/systemd/man/systemd.unit.html#Unit%20File%20Load%20Path
