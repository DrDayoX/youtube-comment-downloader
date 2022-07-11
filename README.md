# youtube-comment-downloader
Simple script for downloading Youtube comments without using the Youtube API with expanded selectors and more. The output is in line delimited JSON or JSON array/list.

## Installation

Preferably inside a [python virtual environment](https://virtualenv.pypa.io/en/latest/) install this package via:

```
pip install https://github.com/eiskaffe/youtube-comment-downloader/archive/master.zip
```

## Usage
```
$ youtube-comment-downloader --help
usage: youtube-comment-downloader [--help] [--output OUTPUT [OUTPUT ...]] [--limit LIMIT] [--language LANGUAGE] [--sort SORT] [--append APPEND] [--heart HEART]
                                  [--author AUTHOR | --authorincl AUTHORINCL | --authorexcl AUTHOREXCL | --authorexclmatch AUTHOREXCLMATCH]
                                  [--comment COMMENT | --commentincl COMMENTINCL | --commentexcl COMMENTEXCL | --commentexclmatch COMMENTEXCLMATCH] [--minlikes MINLIKES] [--maxlikes MAXLIKES]
                                  [--verbose | --quiet] [--presearch] [--format]
                                  [youtubeid ...]
```

For example:
```
youtube-comment-downloader ScMzIvxBSi4
```

### Options 
* `youtubeid`: Positional argument. Multiple YouTube IDs can be set.
* `--help` `-h`: Prints out the help.
* `--output` `-o`: Sets the output file names. The same amount of output file names have to be set for the same amount YouTube IDs.
* `--limit` `-l`: Sets the limit for the amount of maximum comments that can be downloaded. By default it downloads until interrupted.
* `-language`: Language for Youtube generated text (e.g. en)
* `--sort` `-s`: Whether to download popular (0) or recent comments (1). Defaults to 1
* `--append`: Can be used only when one ID is given. Appends the newly downloaded comments to the original file that was given.
* `--presearch`: If selected the program will check for specifics while downloading, and saves only comments that match the specifications. By default it searches trough the comments after all have been downloaded. Use only if you are sure, you'll find what you are looking for!
* `--format`: Formats the output file in to a JSON array.
* `--verbose` `-v`: Verbose mode (Mutually exclusive with quiet)
* `--quiet` `-q`: Quiet mode (Mutually exclusive with verbose)

### Selectors
**Author selectors**
* `--author` `--authormatch` `-a` `-aM`: Only saves the comment if the author's name matches the given string
* `--authorincl` `-aI`: Only saves the comment if the author's name contains the given string
* `--authorexcl` `-aE`: Only saves the comment if the author's name not contains the given string
* `--authorexclmatch` `-aEM`: Only saves the comment if the author's name not matches the given string

**Comment selectors** 
* `--comment` `--commentmatch` `-c` `-cM`: Only saves the comment if the comment matches the given string
* `--commentincl` `-cI`: Only saves the comment if the comment contains the given string
* `--commentexcl` `-cE`: Only saves the comment if the comment not contains the given string
* `--commentexclmatch` `-cEM`: Only saves the comment if the comment not matches the given string

**Like selectors**
* `--minlikes` `-min`: Sets the minimum like requirement for the comment (inclusive)
* `--maxlikes` `-max`: Sets the maximum amount of likes a comment can have (inclusive)

**Heart selector**
* `--heart` `-H`: If set 1, only saves comment with hearts, if 0 it saves comments only without a heart. Default: -1 (Saves all).

## Dependencies
* Python 3.9+
* requests
* dateparser
* alive-progress

The python packages can be installed with:

    pip install -r requirements.txt
