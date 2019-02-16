# Checkpoints
### How To Sync Quickly
##### You can sync a fresh chain from 0 much quicker by loading "checkpoints" with your daemon.

### Setup

- Right click [this link](https://github.com/plenteum/checkpoints/raw/master/checkpoints.csv) and choose `Save link as...` to download the latest checkpoints.csv.
- Place checkpoints.csv in the same folder as your Plenteumd daemon
- You can get Plenteumd from here if you don't have it already: https://github.com/plenteum/plenteum/releases
- Make sure you shut down any GUI wallets, or any other instances of Plenteumd.

### Usage

#### Windows

- First, open a command prompt in the same directory as Plenteumd.
- This can easily be done by moving to the Plenteumd directory in Windows Explorer, then typing `cmd` in the search bar and hitting enter:
- Finally, type `Plenteumd.exe --load-checkpoints checkpoints.csv` in the command prompt.

#### Linux, Apple

- First, open a command prompt in the same directory as Plenteumd.
- You can use the `cd` command to change to this directory. For example, `cd downloads/plenteum-v0.3.0`
- Alternatively, your file manager may provide the ability to open a terminal in your current directory. Navigate to the folder with Plenteumd in, and try right clicking, to see if you can open a terminal there:
- Finally, type `./Plenteumd --load-checkpoints checkpoints.csv` in the terminal.

### Expected Output

If you did the steps correctly, you should see something like this output.

```
2018-May-13 11:58:39.654478 INFO    Welcome to Plenteum v0.3.0 ()
2018-May-13 11:58:39.654914 INFO    Module folder: Plenteumd
2018-May-13 11:58:39.655249 INFO    Loading Checkpoints for faster initial sync...
2018-May-13 11:58:40.854979 INFO    Loaded 144695 checkpoints from checkpoints.csv
```

- Plenteumd will then start syncing from checkpoints.
- If you are using the CLI wallet, then you can just wait for it to finish syncing, and open your wallet.
- If you are using a GUI wallet, let it finish syncing, then open your GUI wallet.

### Common Errors

#### Invalid checkpoint file format

```
2018-May-13 12:10:08.325056 INFO    Loading Checkpoints for faster initial sync...
2018-May-13 12:10:08.339667 ERROR   Invalid checkpoint file format
2018-May-13 12:10:08.341758 ERROR   Exception: Failed to load checkpoints
```

- If you see output like the above, the file you are opening is either not a .csv file, or hasn't been downloaded correctly.
- Ensure you downloaded the file by right clicking, and choosing `Save link as...`.
- If you incorrectly chose the wrong file, you can accidentally  download a html page instead.
- When you open up the file, it should have lots of lines like this:

```
0,4755c750a1ed8535ba1789570899720f3cd010ccf7ab70a1a2d2d53f298eafd5
1,ac804cf393ea5b47e9bf9007f022768f4947cff09b1c916ff9b734ece6c0ddc8
2,cf471a638ab1a4c94450f31f1b97d808912a44c0750839af607488976ea80232
```

- If you absolutely can't get it working, you can make a new text file, copy all the content from here into it: https://raw.githubusercontent.com/plenteum/checkpoints/master/checkpoints.csv
- Then save as checkpoints.csv (Select filetype: all files in windows)

#### Failed to load checkpoints

```
2018-May-13 12:14:57.544286 INFO    Loading Checkpoints for faster initial sync...
2018-May-13 12:14:57.544569 ERROR   Could not load checkpoints file: checkpoints.csv
2018-May-13 12:14:57.544823 ERROR   Exception: Failed to load checkpoints
```

- If you see output like the above, it means the file isn't present in the directory you are in.
- Make sure you have placed the checkpoints.csv file in the same directory as Plenteumd.

#### Plenteumd.exe is not recognized / No such file or directory

```
C:\Users\gentoo>Plenteumd.exe --load-checkpoints checkpoints.csv
'Plenteumd.exe' is not recognized as an internal or external command,
operable program or batch file.
```

`bash: ./Plenteumd: No such file or directory`

- If you see output like one of the above, it means your terminal isn't in the same folder as the Plenteumd program.
- You can type `pwd` to see what folder you are currently in.
- Try following the steps above to get into the right folder, then try again.
- If you type `ls`, you should see the Plenteumd program, if you are in the correct folder:

```
[plenteum-v0.3.0]λ ls
miner  poolwallet  zedwallet  Plenteumd  wallet-service
```

#### IO error

```
2018-May-13 11:58:40.857058 INFO    Opening DB in /home/david/.Plenteum/DB
2018-May-13 11:58:40.858174 ERROR   DB Error. DB can't be opened in /home/zach/.Plenteum/DB. Error: IO error: While lock file: /home/zach/.Plenteum/DB/LOCK: Resource temporarily unavailable
2018-May-13 11:58:40.873692 ERROR   Exception: IO error
```

- If you see output like the above, something else has got the database open already.
- Make sure you have closed down any other Plenteumd's, GUI wallets, and wallet-service.
- Use a task manager to help you find any which might be running in the background, then try again.
