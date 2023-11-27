The Anaconda Prompt and Anaconda PowerShell Prompt serve as parameter-enhanced versions of Windows CMD and PowerShell.
```
%windir%\System32\cmd.exe "/K" <USER>\anaconda3\Scripts\activate.bat <USER>\anaconda3

%windir%\System32\WindowsPowerShell\v1.0\powershell.exe -ExecutionPolicy ByPass -NoExit -Command "& '<USER>\anaconda3\shell\condabin\conda-hook.ps1' ; conda activate '<USER>\anaconda3' "
```

VSCode automatically recognizes terminals for major programming languages, but it does not include Anaconda by default. To integrate the Anaconda PowerShell prompt, open the command panel with `Ctrl+Shift+P`, and search for `Preference: Open User Settings (JSON)`, which opens `settings.json`. 

Add the `Anaconda PowerShell Prompt` configuration from the following code under the `terminal.integrated.profiles.windows` key, and also establish the `terminal.integrated.defaultProfile.windows` key as demonstrated. 
```
    "terminal.integrated.profiles.windows": {
        "PowerShell": {
            "source": "PowerShell",
            "icon": "terminal-powershell"
        },
        "Command Prompt": {
            "path": [
                "${env:windir}\\Sysnative\\cmd.exe",
                "${env:windir}\\System32\\cmd.exe"
            ],
            "args": [],
            "icon": "terminal-cmd"
        },
        "Git Bash": {
            "source": "Git Bash"
        },
        // "Anaconda": {
        //     "path": [
        //         "${userHome}\\anaconda3\\Scripts\\activate.bat"
        //     ],
        //     "args": [],
        //     "icon": "terminal-cmd"
        // },
        // Commented out because doesn't work
        "Anaconda PowerShell Prompt": {
            "source": "PowerShell",
            "args": ["-ExecutionPolicy", "ByPass", "-NoExit", "-Command", "& '<USER>\\anaconda3\\shell\\condabin\\conda-hook.ps1' ; conda activate '<USER>\\anaconda3' "],
            "icon": "terminal-powershell"
        },
    },
    "terminal.integrated.defaultProfile.windows": "Anaconda PowerShell Prompt",
```

The `Anaconda PowerShell Prompt` creates an option for initiating an Anaconda PowerShell Prompt in VSCode terminal. 

The `terminal.integrated.defaultProfile.windows` setting designates Anaconda PowerShell as the default terminal in VSCode.

