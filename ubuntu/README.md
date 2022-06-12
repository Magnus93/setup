## Remove Popping sound from speakers

Temporary solution:
```
echo "0" | sudo tee /sys/module/snd_hda_intel/parameters/power_save
```

Permanent solution:
```
echo "options snd_hda_intel power_save=0" | sudo tee -a /etc/modprobe.d/audio_disable_powersave.conf
```

[annoying-click-popping-sound-on-ubuntu-20-04](https://askubuntu.com/questions/1230833/annoying-click-popping-sound-on-ubuntu-20-04)


## VS Code

Settings:
- editor.minimap.enabled - `false`
- Word wrap - `on`
- Title Bar Style - `Custom`

Install context menu entry in nautilus
```
wget -qO- https://raw.githubusercontent.com/cra0zy/code-nautilus/master/install.sh | bash
```

## NPM
```
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo "export PATH=~/.npm-global/bin:$PATH" >> ~/.profile
source ~/.profile
npm install -g npm-check-updates typescript
npm install -g @typeup/cli @payfunc/cli-card @payfunc/cli
```