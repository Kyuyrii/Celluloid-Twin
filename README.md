# Celluloid Twin

Celluloid (formerly GNOME MPV) is a simple GTK+ frontend for mpv. Celluloid
interacts with mpv via the client API exported by libmpv, allowing access to
mpv's powerful playback capabilities.

Celluloid Twin is an old version of Cellululoid, which is not Libadwaita and uses GTK themes, the 0.21 version.

## Dependencies

- appstream-glib<sup>[[1]](#note1)</sup> (build)
- autoconf >= 2.69<sup>[[1]](#note1)</sup> (build)
- autoconf-archive<sup>[[1]](#note1)</sup> (build)
- automake >= 1.12<sup>[[1]](#note1)</sup> (build)
- pkg-config (build)
- gcc (build)
- glib >= 2.44
- gtk >= 3.22
- mpv >= 0.32
- epoxy
- lua (optional)
- youtube-dl (optional)

<a name="note1">[1]</a>: Not required when building from release tarballs

## Installation

### Snap

<a href="https://snapcraft.io/celluloid-twin">
    <img alt="Get it from the Snap Store" src=https://snapcraft.io/en/dark/install.svg />
  </a>

### My thanks to Sameersharma2006 for the snapcraft.yaml he made:
https://codeberg.org/sameersharma2006/celluloid-snap/src/branch/main/snapcraft.yaml


### Source code
Run the following command in the source code directory to build and install:

```sh
meson build && cd build && ninja && sudo ninja install
```

Alternatively, you can use Autotools:

```sh
./autogen.sh && make && sudo make install
```

When building from release tarballs, replace `./autogen.sh` with `./configure`:

```sh
./configure && make && sudo make install
```

## Usage

### Opening files

There are 4 ways to open files in Celluloid.

1. Passing files and/or URIs as command line arguments.
2. Using the file chooser dialog box, accessible via the "Open" menu item.
3. Typing URI into the "Open Location" dialog box, accessible via the
   menu item with the same name.
4. Dragging and dropping files or URIs onto Celluloid.

### Manipulating playlist

The playlist is hidden by default. To show the playlist, click the "Playlist"
menu item or press F9. Files can be added by dragging and dropping files or URIs
onto the playlist. Dropping files or URIs onto the video area will replace the
content of the playlist. Playlist files or online playlists (eg. YouTube's
playlist) will be automatically expanded into individual items when loaded.

Items in the playlist can be reordered via drag-and-drop. To remove items from
the playlist, select the item by clicking on it then press the delete button on
your keyboard.

### Configuration

Celluloid can be configured using the preferences dialog accessible via the
"Preferences" menu item. Additional configuration options can be set from an
external file using the same syntax as mpv's `mpv.conf`.
See [mpv's manual](https://mpv.io/manual/stable/) for the full list of options.
The file must be specified and enabled in the preferences dialog under the "MPV
Configuration" section.

It is also possible to set mpv options by putting the options &mdash; as you
would pass to mpv on the command line &mdash; in `Extra MPV Options` text box in
the preferences dialog. You can also pass options directly on the command line
by adding `mpv-` prefix to the option name. For example, using the option
`--mpv-vf=flip` when launching Celluloid is equivalent to using `--vf=flip` in
mpv.

### User Scripts

Celluloid can use most mpv user scripts as-is. Some user scripts may define
keybindings that conflict with Celluloid, in which case you'll need to resolve
the conflict by explicitly defining new keybindings using `input.conf`. See
[mpv's manual](https://mpv.io/manual/stable/#lua-scripting-[,flags]]%29) for
more details.

User scripts can be installed by switching to the "Plugins" tab in the
preferences dialog and dropping the files there. A list of mpv user scripts can
be found [here](https://github.com/mpv-player/mpv/wiki/User-Scripts).

### Keybindings

Celluloid defines a set of keybindings in the macro `DEFAULT_KEYBINDS`, which
can be found in
[src/celluloid-def.h](https://github.com/celluloid-player/celluloid/blob/master/src/celluloid-def.h).
The syntax used is exactly the same as mpv's `input.conf`. These keybindings are
applied on top of default keybindings provided by mpv.

Additional keybindings can be defined in an external file using mpv's
`input.conf` syntax. The file can be set in the preferences dialog under the
"Keybindings" section.

## License

Celluloid is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

Celluloid is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with Celluloid.  If not, see <http://www.gnu.org/licenses/>.
