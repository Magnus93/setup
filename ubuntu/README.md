## Remove Popping sound from speakers

Temporary solution:
``` bash
echo "0" | sudo tee /sys/module/snd_hda_intel/parameters/power_save
```

Permanent solution:
``` bash
echo "options snd_hda_intel power_save=0" | sudo tee -a /etc/modprobe.d/audio_disable_powersave.conf
```

[annoying-click-popping-sound-on-ubuntu-20-04](https://askubuntu.com/questions/1230833/annoying-click-popping-sound-on-ubuntu-20-04)

# Setup Teminal Prompt 
**Show git-branch and new line:**
Make copy of `.bashrc` in case of fuckup.
``` bash
cp .bashrc .bashrc_backup
```

To edit:
``` bash
nano .bashrc
```

Replace the `color_prompt` if block with this: 
``` shell
# Add git branch if its present to PS1
parse_git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

if [ "$color_prompt" = yes ]; then
 PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[01;33m\]$(parse_git_branch)\[\033[00m\]\n\$ '
else
 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w$(parse_git_branch)\n\$ '
fi
```

Rerun .bashrc:
``` bash
source .bashrc
```


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
``` bash
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo "export PATH=~/.npm-global/bin:$PATH" >> ~/.profile
source ~/.profile
npm install -g npm-check-updates typescript
npm install -g @typeup/cli @payfunc/cli-card @payfunc/cli
```