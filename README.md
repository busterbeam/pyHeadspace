# headspace-dl
Python command line script to download heaspace packs and singles.
<p align="center">
<img src = "images/demo-f.gif" alt = "demo">
</p>

## Installation
### Install with pip
```sh
pip install headspace-dl
```
### Install latest version
1. Clone this repo:
   ```sh
   git clone https://github.com/yashrathi-git/headspace-dl 
   ```
2. Navigate to the cloned folder.
3. To install run:
   ```sh
   pip install --editable .
   ```

## Setup
After we have installed `headspace-dl`, this is important step to set it up:

1. Go to https://my.headspace.com/ and login to your account.
2. Press `Ctrl + Shift + I` or `Command + Shift + C` to open dev tools
3. Go to the networks tab and **reload the website**
4. Now look for GET request to https://api.prod.headspace.com
5. In **request header** copy the value of authorization parameter. **Make sure you copy it from request headers not response headers**. It would look like this:
   ```
   bearer eyJhbGciOi...
   ```

6. Run:
   ```sh
   headspace
   ```
7. When you run it the first time, it will give you location for `bearer_id.txt` file. Open this file.
8. Paste `authorization` value here and save the file. Setup is done!


**NOTE**:<br />
`authorization` token could invalidate in the future. So if you get an authentication error, please repeat the above steps. 

## Usage
First, make sure to follow <a href="#setup">setup instructions</a><br>
### Downloading Headspace packs
```sh
headspace pack <URL> [Options]
```
**Basic:**
```sh
# Download with all session of duration 15 minutes
headspace pack https://my.headspace.com/packs/33 --duration 15 

# Download sessions of multiple duration
headspace pack https://my.headspace.com/packs/33 --duration "[20, 15, 10]"    

```
**Options:**
```sh
  -d, --duration        Duration or list of duration 
  --no_meditation       Only download meditation session without any techniques
                        videos.

  --no_techniques       Only download techniques and not meditation sessions.
  --out TEXT            Download directory
  --help                Show this message and exit.

```

### Download single session
```sh
headspace download <URL> [options]
```
**Basic:**
```sh
headspace download https://my.headspace.com/play/520 --duration 15
# Download sessions of multiple durations
headspace download https://my.headspace.com/play/520 --duration "[15,20]"
```
**Options:**
```sh
--out TEXT           Download directory.
--id INTEGER         ID of the video. Not required if URL is provided.
-d, --duration       Duration or list of duration
--help               Show this message and exit.
```