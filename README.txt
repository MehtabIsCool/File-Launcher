EAGLERCRAFT LAUNCHER — SETUP

FOLDER LAYOUT
  eaglercraft-launcher.html          the launcher itself — open this
  eaglercraft-launcher_files/        dependency folder the launcher needs to run
    background.jpg                  (optional) custom hero background
    logo.png                        (optional) custom logo icon
    versions/                       your Eaglercraft build .html files go here

This mirrors how Eaglercraft itself ships: a single .html file next to a
matching "..._files" folder it depends on. Don't rename or move
eaglercraft-launcher_files relative to the .html file, or it won't find
its assets or versions.

ADDING A VERSION
Drop the version's .html file straight into
"eaglercraft-launcher_files/versions/" — along with its own companion
"..._files" folder if it has one (that's normal, it's how Eaglercraft
builds work). Only .html files sitting directly inside the versions
folder get picked up; the launcher ignores their companion folders.

USING IT
Just double-click eaglercraft-launcher.html — no server needed. Click
the "LAUNCH EAGLER" card:
  - First time (or if nothing's remembered yet), this opens a folder
    picker — select the "versions" folder itself
    (eaglercraft-launcher_files/versions). Every .html file found there
    gets remembered.
  - After that, clicking the card launches the selected version.

Remembered versions persist across page reloads, even if you later move
or delete the actual file — they stay listed until you remove them
yourself. On the Installations tab, each entry has a Delete button that
forgets it (this only removes it from the launcher's memory, it does not
touch the file on disk). There's also a Refresh button if you add more
versions later and want to scan again, and a Clear All button to wipe
the whole remembered list in one go.

Note: file:// pages share one storage origin across your whole computer
in most Chromium browsers, so without extra care, two different copies
of this launcher folder could end up reading and writing the exact same
remembered list. This launcher scopes its storage to its own file path
to avoid that — if you still see entries from another build bleeding
through, hit Clear All to reset.

Browsers won't let a page silently read your files with zero clicks —
that's a deliberate security restriction, not a bug — so the very first
click (when nothing's remembered yet) is what triggers the folder
picker. It uses a plain folder-picker dialog rather than the newer File
System Access API, which is why it works directly as a file:// page
instead of needing a local server.

CUSTOMIZING THE LOOK
  eaglercraft-launcher_files/background.jpg  → replaces the icy CSS hero
  eaglercraft-launcher_files/logo.png         → replaces the pixel-icon logo
Both optional — the launcher falls back gracefully if they're missing.
