# Open Data Exercise

A foray into the world of open data, using Java programming. The [NYC Open Data](https://opendata.cityofnewyork.us/) portal "_makes the wealth of public data generated by various New York City agencies and other City organizations available for public use._"

## Data source

We analyze and visualize NYC Open Data's [Bi-Annual Pedestrian Counts](https://data.cityofnewyork.us/Transportation/Bi-Annual-Pedestrian-Counts/2de2-6x2h). While the data is published in a variety of formats, we will use the `CSV` version of the data.

This particular data set represents counts of pedestrians at 114 different locations within New York City, taken twice-yearly since 2007. Each twice-yearly count includes data from one weekday (both the morning and in evening, counted separately) and on one weekend day (at around mid-day).

### Schema

A CSV file [mis-]named [PedCountLocationsMay2015.csv](data/PedCountLocationsMay2015.csv), has been downloaded and placed within the `data` directory at the time of this writing. **Do not edit this file**!

The CSV file is structured as follows.

| the_geom                                     | Borough | Loc | OBJECTID | Street_Nam        | From_Stree        | To_Street       | Index | May07_AM | May07_PM | May07_MD | Sept07_AM | Sept07_PM | Sept07_MD | May08_AM | May08_PM | May08_MD | Sept08_AM | Sept08_PM | Sept08_MD | May09_AM | May09_PM | May09_MD | Sept09_AM | Sept09_PM | Sept09_MD | May10_AM | May10_PM | May10_MD | Sept10_AM | Sept10_PM | Sept10_MD | May11_AM | May11_PM | May11_MD | Sept11_AM | Sept11_PM | Sept11_MD | May12_AM | May12_PM | May12_MD | Sept12_AM | Sept12_PM | Sept12_MD | May13_AM | May13_PM | May13_MD | Sept13_AM | Sept13_PM | Sept13_MD | May14_AM | May14_PM | May14_MD | Sept14_AM | Sept14_PM | Sept14_MD | May15_AM | May15_PM | May15_MD | Sept15_AM | Sept15_PM | Sept15_MD | May16_AM | May16_PM | May16_MD | Sept16_AM | Sept16_PM | Sept16_MD | May17_AM | May17_PM | May17_MD | Sept17_AM | Sept17_PM | Sept17_MD | May18_AM | May18_PM | May18_MD | Sept18_AM | Sept18_PM | Sept18_MD | May19_AM | May19_PM | May19_MD | Oct20_AM | Oct20_PM | Oct20_MD | May21_AM | May21_PM | May21_MD |
| :------------------------------------------- | :------ | :-- | :------- | :---------------- | :---------------- | :-------------- | :---- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :-------- | :-------- | :-------- | :------- | :------- | :------- | :------- | :------- | :------- | :------- | :------- | :------- |
| POINT (-73.90459140730678 40.87919896648574) | Bronx   | 1   | 1        | Broadway          | West 231st Street | Naples Terrace  | N     | 1189     | 4094     | 2508     | 734       | 2646      | 2939      | 802      | 4015     | 2631     | 1125      | 4310      | 3420      | 1001     | 3475     | 2832     | 991       | 4262      | 2469      | 1010     | 3609     | 3128     | 863       | 4119      | 2217      | 997      | 4440     | 2687     | 1328      | 3820      | 2428      | 1288     | 3328     | 3365     | 1268      | 4315      | 2276      | 1210     | 4710     | 3825     | 1206      | 4590      | 3008      | 1220     | 4384     | 2641     | 1450      | 4646      | 2996      | 1788     | 4980     | 3033     | 1204      | 4520      | 2999      | 1246     | 4531     | 2686     | 1309      | 3642      | 2830      | 1916     | 5893     | 2776     | 1111      | 4044      | 2731      | 1271     | 4502     | 2899     | 1708      | 4464      | 2967      |          |          |          | 486      | 2843     | 1754     | 630      | 3262     | 1710     |
| POINT (-73.92188432870218 40.82662794123294) | Bronx   | 2   | 2        | East 161st Street | Grand Concourse   | Sheridan Avenue | Y     | 1511     | 3184     | 1971     | 1855      | 3754      | 1183      | 1136     | 2638     | 1522     | 1939      | 3283      | 1383      | 1351     | 3111     | 1304     | 1227      | 3137      | 2762      | 2077     | 3283     | 1409     | 1007      | 3069      | 1477      | 1734     | 3333     | 1772     | 2051      | 3525      | 1752      | 1233     | 1875     | 1912     | 2113      | 4099      | 1970      | 2278     | 4215     | 2288     | 2071      | 3890      | 1832      | 2206     | 4363     | 2315     | 1949      | 4435      | 2388      | 2318     | 4589     | 2483     | 2005      | 4790      | 2512      | 2053     | 4721     | 2311     | 2109      | 5485      | 2548      | 1848     | 4920     | 2143     | 2389      | 5952      | 2832      | 1749     | 5148     | 2156     | 2006      | 4723      | 1604      | 1702     | 4347     | 1576     | 780      | 1892     | 1287     | 1405     | 2097     | 1410     |
| POINT (-73.89535781584335 40.86215460031517) | Bronx   | 3   | 3        | East Fordham Road | Valentine Avenue  | Tiebout Avenue  | Y     | 1832     | 12311    | 14391    | 1829      | 9215      | 15065     | 1061     | 8013     | 7927     | 2497      | 10010     | 8013      | 1689     | 8374     | 7472     | 2387      | 10655     | 6614      | 2285     | 10943    | 10424    | 2807      | 12658     | 7714      | 2289     | 15890    | 9167     | 2679      | 13548     | 8140      | 2125     | 7635     | 7022     | 2704      | 10486     | 7421      | 2710     | 12723    | 8872     | 2651      | 10613     | 8241      | 2699     | 12490    | 6339     | 2752      | 10408     | 8266      | 2382     | 11216    | 7574     | 2733      | 10586     | 9072      | 2540     | 11272    | 8422     | 2422      | 11145     | 9775      | 2557     | 12125    | 6499     | 2783      | 12388     | 7076      | 2209     | 9634     | 7066     | 2246      | 8931      | 6212      | 1625     | 11739    | 7468     | 972      | 6976     | 5058     | 942      | 5576     | 4402     |
| ... and so on ...                            | ...     | ... | ...      | ...               | ...               | ...             | ...   | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...       | ...       | ...       | ...      | ...      | ...      | ...      | ...      | ...      | ...      | ...      | ...      |

According to [the description of the metadata](http://www.nyc.gov/html/dot/downloads/pdf/bi-annual-ped-count-readme.pdf), the fields include:

- **the_geom** – Geospatial coordinates (longitude, latitude) of the location
- **Borough** – Borough count conducted in
- **Loc** – Count location identifier, ranging from 1-114
- **Street_Nam** – Street counts conducted on
- **From\_/To_Street** – Block of street counts conducted
- **Index** – Indicates if location is included in Mayor’s Management Report Pedestrian Index
- **(Month)(Year)\_AM** – weekday morning count, in the month/year indicated
- **(Month)(Year)\_PM** – weekday evening count, in the month/year indicated
- **(Month)(Year)\_MD** – weekend count, in the month/year indicated


## Interactivity

While viewing the map, the user must be able to select which of the visualizations to view by typing the letters `1` through `6` on the keyboard.

- A method named `keyPressed` has been given to you in the code.
- This function will be automatically run every time the user presses a key.
- Comments in the code indicate how to detect which key was pressed using the `key` variable.
- The key that was pressed is represented as a `char` data type.

## Technical requirements

This project depends upon the [Unfolding](http://unfoldingmaps.org/) library, which itself depends upon the core library of the [Processing](https://processing.org/) project. These dependencies are included within the `lib` directory.

However, Processing currently works only with Java 8. In order to have the Java Extensions for Visual Studio Code run the program with Java 8, instead of any newer version, you must do the following:

1. Download and install the [jdk8u242-b08 version of OpenJDK 8](https://github.com/AdoptOpenJDK/openjdk8-binaries/releases/tag/jdk8u242-b08) - on MacOS, select the appropriate `.pkg` file; for Windows, select the appropriate `.msi` file (be sure to select the file with `jdk` in its name, not the one with `jre` in its name).
1. Note the file path to the directory where this new JDK was installed. We'll refer to this directory later as `THE_PATH_TO_JDK_8`.
   - On Mac, it is probably in `"/Library/Java/JavaVirtualMachines/adoptopenjdk-8.jdk/Contents/Home"`. Note the inclusiong of `Contents/Home` at the end of the path - we'll need it with this addition in the settings file.
   - On Windows, it is probably in `C:\Program Files (x86)\AdoptOpenJDK\jdk-8.0.242.08-hotspot`, which would have to have its back slashes escaped to be `"C:\\Program Files (x86)\\AdoptOpenJDK\\jdk-8.0.242.08-hotspot"` in the settings file.
1. In Visual Studio Code, go to Settings (MacOS: `Code`->`Preferences`->`Settings`; Windows: `File`->`Preferences`->`Settings`), and enter "`java jdt ls java home` in the search field. You should see an option with a link to `Edit in settings.json` - click that link to open that file in the editor.
1. In the `settings.json`, edit the "`java.configuration.runtimes`" setting so that it includes the new JDK. If there is no such setting currently, add it. If the setting exists, and an existing JDK is listed there, you an keep both. For example (replace `THE_PATH_TO_JDK_8` with the correct path for your newly-installed JDK) :
   ```javascript
   "java.configuration.runtimes": [
       {
       "name": "JavaSE-1.8",
       "path": "THE_PATH_TO_JDK_8",
       "default": true
       },
       {
       "name": "JavaSE-15",
       "path": "THE_PATH_TO_AN_EXISTING_JDK",
       "default": false
       }
   ],
   ```
1. With this project open, go to Visual Studio Code's Command Palette (`View`->`Command Palette`) and search for "`Java: Configure Java Runtime`". Click on the matching option that appears.
1. In the `Configure Java Runtime` setting document, click the icon to edit the current runtime setting for this project and change it to the newly-installed JDK.
1. In the Command Palette again (`View`->`Command Palette`), search for "`Java: Clean Language Server Workspace`". Click the matching option that appears and confirm that you would like to reset the Java language server.


## Sample visualizations

The following screenshots show the first 4 visualizations:

1. May 2021 Morning Pedestrian Counts:
   ![May 2021 Morning Pedestrian Counts](./images/screenshot_may2021morning.png)
2. May 2021 Evening Pedestrian Counts:
   ![May 2021 Evening Pedestrian Counts](./images/screenshot_may2021evening.png)
3. Difference between May 2021 Evening and Morning Pedestrian Counts
   ![Difference between May 2021 Evening and Morning Pedestrian Counts](./images/screenshot_may2021eveningvsmorning.png)
4. Difference Between May 2021 and May 2019 Pedestrian Counts:
   ![Difference Between May 2021 and May 2019 Pedestrian Counts](./images/screenshot_may2021vsmay2019.png)
