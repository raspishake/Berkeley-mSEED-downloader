# Berkeley mSEED Downloader
### Developed for Angela Chung at Berkeley Seismology Lab for testing the use of RS data in an Earthquake Early Warning (EEW) application in California.

*Coded by Giuseppe Petricca (@gmrpetricca)*

[![GitHub](https://img.shields.io/github/license/raspishake/rsudp)](https://github.com/raspishake/rsudp/blob/master/LICENSE)

This script will read data both from the Raspberry Shake AM network servers and from the attached `.xlsx` file. It will automatically download a list of .mSEED files in relation to user-input earthquake details and range in km.

Required software and packages:
- Python 3
- Jupyter
- Obspy
- Matplotlib
- Numpy
- Pandas
- urllib

Installation via Anaconda:
```bash
# install the environment with the correct software:
conda create -n berkeleymseed python=3 jupyter matplotlib obspy numpy pandas urllib
# activate the environment
conda activate berkeleymseed
# start Jupyter Notebook
jupyter-notebook
```

Once this is done, it is possible to open the `.ipynb` file in the repository. Microsoft Excel is required to open the `.xlsx` file, please keep the two in the same folder.

The process and file are commented throughout the various steps, however, this is a brief guide to use them: 

1. Open the `.xlsx` file and add the UTC Date/Time (with the format `YYYY-MM-DDThh-mm-ss.ddd`) of an earthquake, together with Latitude and Longitude of its epicenter, in decimals (i.e. `34.256`, `116.289`)
2. The earthquake list can be as long as it is desired. Please do not insert empty rows between an event and another. Three test events are listed for demonstration purposes.
3. Save the `.xlsx` file and open the `.ipynb` file. Nothing should be modified in this file unless a particular condition is required.
4. Execute the script. 
5. For each event, the script will ask the user for a range in km in which it will try to find any Raspberry Shake unit that was connected at the time. In the case of not finding any, the script will prompt the user.
6. At the end of the process, every event `.mseed` downloaded files, for each channel of each Shake unit included in the km range, will be put in a separate folder, with the following naming convention: `YYYYMMDDhhmmssddd.network.stationcode.channel.mseed`
7. Another `.xlsx` file will be created in each event folder, now listing all the Shake units in the input range, alongside their connectivity status and their channels. 
8. If needed, is possible to add new Raspberry Shake units in the second sheet of the `.xlsx` file, in the same format as the previous entries.

Done!

