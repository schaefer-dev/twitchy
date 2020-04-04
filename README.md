# twitchy
Lists twitch channels that are currently online

**python >= 3.6, python-requests**

Features:
* Tracking of most watched channels.
* Custom layouts: User adjustable colors and columns
* Sync your followed accounts to a local sqlite database that does not judge you.
* The ability to display alternate names for games / streamers. If your happiness is somehow contingent upon displaying "Hearthstone: Heroes of Warcraft" as "Wizard Poker", well, you've come to the right place.

## Installation
1. Clone the repository
2. In the root directory, type:

        $ python setup.py build
        # python setup.py install

3. Launch with `twitchy`

Please delete `~/.config/twitchy3/*` and restart twitchy before reporting any issues.

## Usage

    $ twitchy [ARGUMENT] [OPTIONS]

    [ARGUMENT] to the script is used as a search string for channels in the local database.

    [OPTIONS]
    -h, --help                      This helpful message
    -a <channel name>               Add channel(s)
    -an [*searchstring*]            Set/unset alternate names
    --configure                     Configure options
    -d [*searchstring*]             Delete channel(s) from database
    --non-interactive [go / kickstart]
                                    Generate parsable data for integration elsewhere
    --reset                         Delete everything and start over
    -s <username>                   Sync followed channels from specified account
    -v <channel name>               Watch channel's recorded videos
    -w <channel name>               Watch specified channel(s)

    First run:
    Will create both the database and an editable config file in ~/.config/twitchy3/

    While playing:
    <q / Ctrl + C> to quit

    Run in non-interactive mode. This is useful for integration with dmenu / rofi / conky.
    --non-interactive go            Get customizable comma separated list of channel / game data
    --non-interactive kickstart <>  Start channel directly without asking for confirmation

## Examples

Using no argument while launching the script will check the status of every channel in the local database:
![alt tag](https://i.imgur.com/1Id6J7G.png)

Add channels to local database:

    $ twitchy -a bobross <channel2> <channel3> ...
    $ twitchy -s <your twitch username>
    
If your username is not found, try again using all lowercase letters.

Display all strings matching *obr*:

    $ twitchy obr
    Checking channels...
    Creative
    1 bobross                   80085           The Joy of Painting Monday Season 7 Marathon #painting...
    Sonic: Generations
    2 mariobro                  123             #WhereMuhPrincessAt?
    Wizard Poker
    3 flatulentcobra            6969            Playing secret Paladin. Killing a puppy later.
    Channel number(s): 1-h 2-s 3-l

    Custom quality settings: Specify with hyphen next to channel number.
    E.g. <1-h 2-s 3-l> will simultaneously play
    channel 1 in high quality, 2 in source quality, and 3 in low quality.
