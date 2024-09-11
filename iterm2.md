Links: ...
Rel: [[Terminal]]; [[applescript]]; [[pnano]]
Ref: [docs](https://iterm2.com/documentation-scripting.html) (for use with applescript "depreciation warning" = maintenance and no planned feature additions)
- https://dev.to/vivekkodira/automate-a-multi-window-experience-on-iterm2-2j9e
- 

--- 
[[PYTHON]]

```pip install iterm2```
https://iterm2.com/python-api/examples/launch_and_run.html

```# pip3 install pyobjc``` ^^ installs w/
https://pyobjc.readthedocs.io/en/latest/index.html


```py
import iterm2
import AppKit

# Launch the app
AppKit.NSWorkspace.sharedWorkspace().launchApplication_("iTerm2")

async def main(connection):
	app = await iterm2.async_get_app(connection)

	# Foreground the app
	await app.async_activate()

	# This will run 'vi' from bash. If you use a different shell, you'll need
	# to change it here. Running it through the shell sets up your $PATH so you
	# don't need to specify a full path to the command.
	await iterm2.Window.async_create(connection, command="/bin/bash -l -c vi")

# Passing True for the second parameter means keep trying to
# connect until the app launches.
iterm2.run_until_complete(main, True)
```

--- 
Preferences:

Advanced -> Mouse -> Scroll wheel sends arrow keys when in alternate screen mode. (allow trackpad scroll in [[nano]] )
Profiles -> Advanced -> Semantic History -> "Run coprocess..." ```/usr/bin/nano \1``` (cmd+click-> open ```ls``` files direct to [[nano]] )


