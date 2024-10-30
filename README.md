# 'chatGPTclone' interactive CLI

![Screenshot 2024-03-28 alle 09 52 03-EDIT-2](https://github.com/user-attachments/assets/db7e53c3-a871-4506-b41d-08ecf71f4977)

A proof-of-concept project on how to build an <b>interactive CLI for chatGPT</b> queries through their own API, based on a video by Warp: https://www.youtube.com/watch?v=7p7kJvckrFE

This new release of the tool makes quite a few changes to the original code, to allow for:
- correct formatting,
- subsequent questions without the code breaking up,
- some minorly customised output lines,
- <b> a newly updated '--help' command that also lists new versions of chatGPT</b>,
- <b> `/bye` instead of `exit` as a break command, to avoid unvoluntary stops</b>,
- <b>a new shell wrapper handling the python script</b>,
- <b>the use of Python virtual environments (venv) to avoid version conflict (the shell wrapper will install Python package ```pyenv```)</b>,
- <b>iterations to check if the venv is already present</b>,
- and <b>especially code changes to accomodate for Python package ```openai>1.0.0```</b>, since it now requires a different kind of API keys.
More information on the new requirements for the chatGPT API on: https://platform.openai.com/docs/overview?lang=python


## INSTRUCTIONS
### Set-up instructions (MacOS/Linux)
This tool requires <bi>pip</bi> to already be installed on the device, to install Python package ```pyenv```.

Clone the directory with the `git clone https://github.com/NCMBianchi/chatGPTclone.git` command in your terminal. I suggest placing it in your root directory.

Move to the directory with the `cd chatgptclone` command, and then activate the executable with the `chmod +x main.sh` command. Make a `.env` file storing your own 'API project key' from OpenAI's platform –more info on this in a latter section.

I suggest to then add the `alias chatgptclone="cd ~/chatgptclone && ./main.sh"` line to your shell's configuration file (assuming it was installed in the root directory) so that you can exucute all following commands just using the alias in the terminal. I suggest to do this only if you are comfortable editing your shell's configuration file (<i>i.e.</i> `.zshrc` for Zsh, `.bashrc` for Bash, `.config/fish/config.fish` for Fish): if so, edit it with Vim –or any other text editor of choice- adding the alias line at the end of the document. If you are not sure which shell your terminal is using, run the `echo $SHELL` command.

### Use instructions (MacOS/Linux)

Queries can be performed with the `chatgptclone -t "_________"` (`main.sh -t "_______"` if the alias was not setup, as long as you are in the tools directory –which can be accesed with the `cd ~/chatgptclone` command, if the repository was cloned in the root directory), adding your query between quote marks.

| Short command | Full command | Description                                    | Default value |
|---------------|--------------|------------------------------------------------|---------------|
| -t            | --text       | Starts with an initial message text.           |               |
| -T            | --temp       | Sets the temperature (randomness) from 0 to 1. | 0.7           |
| -M            | --maxtokens  | Sets the maximum response length.              | 150           |
| -m            | --model      | Chooses a model.                               | gpt-4o-mini   |

These are all the commands that can be used in the tool, and they all required values to be inputted between quotation marks.

Moreover, the `chatgptclone --help` command allows to display this very table within the tool.

<img width="917" alt="Screenshot 2024-10-28 alle 17 11 15" src="https://github.com/user-attachments/assets/87d6e39b-082f-40d3-b158-f06fd633bece">

### API key instructions
To use this, you have to first get your own API key from OpenAI. They recently shifted from the legacy shorter API keys to the new and longer project API keys: if you have an older key active, I suggest deactivating it and replacing it with a new project one.

<img width="1025" alt="Screenshot 2024-10-28 alle 17 06 57-EDIT" src="https://github.com/user-attachments/assets/b387a067-7145-4af3-a21c-737d8cf51c39">

Then create a <bi>.env</bi> file with this line: `OPENAI_KEY="____"` filling it with your own API key. Place it in the cloned directory's root.

### venv instructions (MacOS/Linux)
If you want to remove the virtual environment created by this tool, just use the `pyenv virtualenv-delete chatgptclone` command in your terminal: this will delete the virtual environment and all the packages within it. If you want to also remove Python package ```pyenv``` entirely, use the `pip uninstall pyenv` command, which requires a Y/n confirmation. First check no other functionality in your device is using them: you can check it with commands `pyenv versions` and `pyenv virtualenvs`.


##
<b> This is NOT a commercial product. The OpenAI logo mixed with the style of the 'Terminal' MacOS app icon in the image at top is used to convey the fact that the API keys used are official, according to fair use. </b>
