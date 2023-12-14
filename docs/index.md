# Welcome to Silimate Platform Docs

This is the documentation website for the Silimate Platform. For any questions, comments, or concerns, please contact support via Slack/[email](mailto:contact@silimate.com).

## Quick Setup: Web GUI

Silimate Platform should be already installed and properly running on your server. If it is not, see [Installation](installation.md) and/or [Infrastructure](infrastructure.md), or contact support.

### Port forwarding (recommended)

To access the GUI on your local machine, you need to provide an SSH tunnel into the server with *port forwarding*. To do this, add the argument `-L 80:192.168.49.2:80` to your `ssh` command, for example:
```sh
sudo ssh -Y -i testing_ec2.pem -L 80:192.168.49.2:80 ec2-user@ec2-XX-XX-X-XXX.us-west-2.compute.amazonaws.com
```
NOTE: you may need root privileges on your local machine to forward to port 80, hence `sudo` in the above command.

Now, you should be able to navigate to [http://localhost](http://localhost) on your local browser and the platform web GUI should appear.

### X11 forwarding/VNC

Assuming you have X11 forwarding/VNC setup between your local machine and the server, you may simply open a browser session on the server (e.g., `firefox`) and navigate to [http://192.168.49.2](http://192.168.49.2).

NOTE: this approach may be less responsive than port forwarding.

## Quick Setup: CLI

Silimate Platform should be already installed and properly running on your server. If it is not, see [Installation](installation.md) and/or [Infrastructure](infrastructure.md), or contact support.

To use the CLI:

- Export `SILIMATE_PASSWORD` in your `.profile` (or equivalent shell init script):
```sh
export SILIMATE_PASSWORD=Silimate1234%4321etamiliS
```
- Ensure `requests` library for `python3` is installed:
```sh
python3 -m pip install requests
```
- Add `/silimate/cli/` to your `$PATH` variable:
```sh
export PATH=$PATH:/silimate/cli
```
- Restart your shell and test with `smake -l`. You should see a list of all the available flows.
