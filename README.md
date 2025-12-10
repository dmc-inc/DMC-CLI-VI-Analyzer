# DMC CLI VI Analyzer

This package introduces a more powerful command-line interface for VI Analyzer, built on the g-CLI framework. It is designed to improve automation, feedback, and control when integrating VI Analyzer into development workflows.

Key Features
- Improved CLI Feedback: Leverages g-CLI to provide more informative and structured output directly in the command line.
- Threshold-Based Evaluation: Supports configurable thresholds for High, Normal, and Low severity categories, enabling nuanced analysis beyond simple pass/fail. Also allows for thresholds to be run against each VI instead of catagories.

This tool is ideal for teams looking to enforce code quality standards in LabVIEW projects with greater flexibility and precision.

This uses a g-cli call in the form:

```
g-cli --arch 64 (optional)--lv-ver [LV_Year] (optional)--timeout [ms Timeout] "DMC CLI VI Analyzer" -- [arguments]
```

This must be called from the working directory you want to analyze.

## Optional Arguments
- **-viancfg** | absolute or relative to working directory relative path to viancfg file.
  - ***Default***: Default.viancfg included with package
- **-reportdir** | absolute or relative to working directory relative path to report output directory. 
  - ***Default***: *WorkingDir*/Reports
- **-included** | comma seperated string of all folders within working directory to include. Recursive search. 
  - ***Default***: Settings within viancfg file
- **-excluded** | comma seperated string of all folders within working directory to exclude.
  - ***Default***: None
- **-high** | High Threshold.
  - ***Default***: 100%
- **-normal** | Normal Threshold.
  - ***Default***: 100%
- **-low** | Low Threshold.
  - ***Default***: 100%
- **-pervi** | Flag to run the thresholds per VI instead of per catagory.
- **-html** | Flag to generate html report.
- **-rsl** | Flag to generate rsl report.
- **-help** | Returns this help information.

## Example Use Cases

### Default HTML Report Run
Will run a standard VI Analyzer on all files under the Working Directory using the Default.vianfg included in the package. No Thresholds are used. A HTML report will be generated in Working Directory / Reports
```
cd <Root Code Directory>
g-cli "DMC CLI VI Analyzer" -- -html
```
#### Example Output
```
Loading VI Analyzer - Default.viancfg
Setting Included Folders...Included 12 files
Loaded 12 files to analyze.
Analyzing...
0.0 % Complete
8.3 % Complete
16.7 % Complete
25.0 % Complete
33.3 % Complete
41.7 % Complete
50.0 % Complete
58.3 % Complete
66.7 % Complete
75.0 % Complete
83.3 % Complete
91.7 % Complete
100.0 % Complete
100% Complete
VI Analyzer completed.
424 tests passed.
8 tests failed.
0 tests skipped.
0 VIs were unloadable.
0 tests were unloadable.
0 tests were unrunable.
0 tests produced error.
Run Time: 01:11.990
Reporting HTML "C:\Projects\Open Source\DMC CLI - Caraya\Source\Reports\VIA_Results_25_12_10_10_41.html"
Exiting VI Analzyer
```

### Threshold HTML Report Run
Will run a standard VI Analyzer on all files under the Working Directory using the Default.vianfg included in the package. Thresholds of 100/90/80 are used. A HTML report will be generated in Working Directory / Reports
```
cd <Root Code Directory>
g-cli "DMC CLI VI Analyzer" -- -high 100 -normal 90 -low 80 -html
```
#### Example Output
```
Loading VI Analyzer - Default.viancfg
Setting Included Folders...Included 12 files
Loaded 12 files to analyze.
Analyzing...
0.0 % Complete
8.3 % Complete
16.7 % Complete
25.0 % Complete
33.3 % Complete
41.7 % Complete
50.0 % Complete
58.3 % Complete
66.7 % Complete
75.0 % Complete
83.3 % Complete
91.7 % Complete
100.0 % Complete
100% Complete
VIA+ Per VI Results:
High Rank - 0 Failures (100.0% Threshold)
Normal Rank - 1 Failures (90.0% Threshold)
Low Rank - 0 Failures (80.0% Threshold)
Total Tests - 12
0 VIs not loadable
0 Tests not loadable
0 Tests no runable
0 Tests produced error
Total Runtime: 01:08.032
Reporting HTML "*WorkingDir*\Reports\VIA_Results_25_12_10_10_44.html"
Exiting VI Analzyer
```

### Per VI Threshold HTML Report Run
Will run a standard VI Analyzer on all files under the Working Directory using the Default.vianfg included in the package. Thresholds of 100/90/80 are used. A HTML report will be generated in Working Directory / Reports
```
cd <Root Code Directory>
g-cli "DMC CLI VI Analyzer" -- -pervi -high 100 -normal 90 -low 80 -html
```
#### Example Output
```
Loading VI Analyzer - Default.viancfg
Setting Included Folders...Included 12 files
Loaded 12 files to analyze.
Analyzing...
0.0 % Complete
8.3 % Complete
16.7 % Complete
25.0 % Complete
33.3 % Complete
41.7 % Complete
50.0 % Complete
58.3 % Complete
66.7 % Complete
75.0 % Complete
83.3 % Complete
91.7 % Complete
100.0 % Complete
100% Complete
VIA+ Per Ranking Results:
High Rank - Pass
   100.0% Passing (168/168) 
   Threshold 100.0%
Normal Rank - Pass
   98.1% Passing (106/108) 
   Threshold 90.0%
Low Rank - Pass
   96.2% Passing (150/156) 
   Threshold 80.0%
0 VIs not loadable
0 Tests not loadable
0 Tests no runable
0 Tests produced error
Total Runtime: 01:07.216
Reporting HTML "*WorkingDir*\Reports\VIA_Results_25_12_10_10_46.html"
Exiting VI Analzyer
```
### Threshold HTML Report Run using Targets viancfg file
Will run a standard VI Analyzer on all files under the Working Directory using the viancfg file found in the working directory. Thresholds of 100/90/80 are used. A HTML report will be generated in Working Directory / Reports
```
cd <Root Code Directory>
g-cli "DMC CLI VI Analyzer" -- -viancfg VIA.viancfg -high 100 -normal 90 -low 80 -html
```
### Include/Exclude
Will run a standard VI Analyzer on all files under the Working Directory using the Default.vianfg included in the package. Thresholds of 100/90/80 are used. A HTML report will be generated in Working Directory / Reports
```
cd <Root Code Directory>
g-cli "DMC CLI VI Analyzer" -- -included "Source" -excluded "Test,Examples" -high 100 -normal 90 -low 80 -html
```

# [Wiki Homepage](../../wikis/Home)

# Author(s), Contributors
* Jonathan Jay


# License
All software in this repository is licensed under the license found in [..\Build\License\](../master/Build/License/). 