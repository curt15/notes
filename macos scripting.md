Links: [[PYTHON]] - [[linux]] - [[GOALS]] 
Rel: [[os]] [[sys]] [[subprocess]] [[macos]]

--- 

```sh

/Users/curt/Library/Mobile\\ Documents/com\\~apple\\~CloudDocs/onotes

```

```py

import subprocess


def get_curr_user():
	      return subprocess.run(['whoami'], capture_output=True).stdout.decode('utf-8').strip()

```

--> a Click project (and explore BASH more before [[Oh My Zsh]] fuzzys)