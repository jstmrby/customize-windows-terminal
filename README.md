# Customize your Windows PowerShell prompt

## Step 1: Set up `posh-git`

Install posh-git as described [here](https://github.com/dahlbyk/posh-git#installing-posh-git-via-powershellget-on-linux-macos-and-windows).

After installing add posh-git to your PowerShell profile as described [here](https://github.com/dahlbyk/posh-git#step-2-import-posh-git-from-your-powershell-profile).

If there is no PowerShell profile the previous step will create one at:

```
%USERPROFILE%\Documents\WindowsPowerShell\
```

---

## Step 2: Customize the prompt

Open the created profile file. The filename will be something like this: `Microsoft.PowerShell_profile.ps1`

If you cannot find the file issue this command in the PS:

```
$PROFILE
```

This will print you the path to your PS profile.

Once you have the file opened you can modify your prompt to your liking.

It should look something like this:

```bash
Import-Module posh-git

$GitPromptSettings.DefaultPromptBeforeSuffix.Text = '`n'            # Prints a new line character before your suffix
$GitPromptSettings.DefaultPromptSuffix = ' $("└─ $") '              # The prompt suffix. Replaces the '>' character
$GitPromptSettings.DefaultPromptSuffix.ForegroundColor = 'Green'    # Suffix text color
$GitPromptSettings.DefaultPromptPrefix.Text = '$env:UserName @ '    # Prints the user's username and a '@' character
$GitPromptSettings.DefaultPromptPrefix.ForegroundColor = 'Green'    # Prefix text color
$GitPromptSettings.DefaultPromptPath.ForegroundColor = 0x3a96dd     # Working directory path text color
```

---

## (Optional) Step 3: Customize Windows Terminal

If you are not using Windows Terminal, I recommend you to take a look at it, as it is a really nice take on a highly customizable terminal. Give it a try, chances are you will like it!

If you already have it, click the downward chevron next to the new tab (`+`) icon and select settings, then click: `Open in JSON`.

Here are my terminal settings as a reference, but feel free to experiment with the settings.

```jsonc
"profiles": {
  "defaults": {},
  "list": [
    {
      "useAcrylic": true,           // Enable the opacity setting
      "acrylicOpacity": 0.8,        // 80% opacity
      "colorScheme": "Campbell",    // Text color scheme
      "cursorColor": "#FFFFFD",     // Color of the cursor
      "font": {
        "face": "Cascadia Code PL"  // This is a downloaded Powerline font. PL fonts go together well with posh-git
      },
      // Everything below this line are default settings
      "commandline": "powershell.exe",
      "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
      "hidden": false,
      "name": "Windows PowerShell"
    },
    {
      "commandline": "cmd.exe",
      "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
      "hidden": false,
      "name": "Command Prompt"
    },
    {
      "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
      "hidden": false,
      "name": "Azure Cloud Shell",
      "source": "Windows.Terminal.Azure"
    }
  ]
}
```
