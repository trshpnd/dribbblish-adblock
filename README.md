## Dribbblish-adblock

My fork of spicetify's "Dribbblish" theme with some adblock features patched from Daksh777/SpotifyNoPremium.

It also features a chill version of gruvbox colorscheme, with less reds :)

For an even better "tracker-free" experience, try it along with spotify-adblock. (abba23/spotify-adblock)

**_This build was tested on linux only._

## Manual Install
Run these commands:

### Linux and MacOS:
In **Bash**:
```bash
cd "$(dirname "$(spicetify -c)")/Themes/Dribbblish"
mkdir -p ../../Extensions
cp dribbblish.js ../../Extensions/.
spicetify config extensions dribbblish.js
spicetify config current_theme Dribbblish color_scheme base
spicetify config inject_css 1 replace_colors 1 overwrite_assets 1
spicetify apply
```
From Spotify > v1.1.62, in sidebar, they use an adaptive render mechanic to actively show and hide items on scroll. It helps reducing number of items to render, hence there is significant performance boost if you have a large playlists collection. But the drawbacks is that item height is hard-coded, it messes up user interaction when we explicity change, in CSS, playlist item height bigger than original value. So you need to add these 2 lines in Patch section in config file:

```ini
[Patch]
xpui.js_find_8008 = ,(\w+=)32,
xpui.js_repl_8008 = ,${1}56,
```

## Change Color Schemes
There are 9 color schemes you can choose: `base`, `white`, `dark`, `dracula`, `nord-dark`, `nord-light`, `samourai`, `purple`, `gruvbox`. Change scheme with commands:
```
spicetify config color_scheme <scheme name>
spicetify apply
```

## Manual uninstall 
Remove the dribbblish script with the following commands 

```
spicetify config extensions dribbblish.js-
```
And remove Patch lines you added in config file earlier. Finally, run:
```
spicetify apply
```
