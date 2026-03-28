# Desktop files

Waydroid stores .desktop files in 2 different locations;

### Applications
`~/.local/share/applications`

### Waydroid itself 
`/usr/share/applications/`

If for whatever reason you need to edit `Waydroid.desktop` please set it to read-only after you're done editing like so;

```
sudo chmod -w /usr/share/applications/Waydroid.desktop
```
