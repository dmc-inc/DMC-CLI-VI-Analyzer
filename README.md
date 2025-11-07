# DMC CLI VI Analyzer

This repository contains the code to use a better CLI VI Analyzer. It is g-cli based and thus returns better feedback in the command line as well as allows for thresholds that operate on the High, Normal, and Low catagories without a full pass/fail.

This uses a g-cli call in the form:

g-cli (optional)--lv-ver [LV_Year] (optional)--timeout [ms Timeout] "DMC CLI VI Analyzer" -- [arguments]

This must be called from the working directory you want to analyze.

-------optional arguments-------
-viancfg <absolute or relative to working directory relative path to viancfg file. defaults to Default.viancfg included with app>
-reportdir <absolute or relative to working directory relative path to report output directory. Defaults to workingdir/Reports>
-included <comma seperated string of all folders within working directory to include. Recursive search. Defaults to settings within viancfg>
-excluded <comma seperated string of all folders within working directory to exclude. Defaults to none>
-high <High Threshold, default 100>
-normal <Normal Threshold, default 90>
-low <Low Threshold, default 80>
-html <Flag to generate html report>
-rsl <Flag to generate rsl report>
-help <Returns this help information>

If no -viancfg or -included is specified, it will run the Default.viancfg on Source.

# [Wiki Homepage](../../wikis/Home)

# Author(s), Contributors
* Jonathan Jay


# License
All software in this repository is licensed under the license found in [..\Build\License\](../master/Build/License/). 