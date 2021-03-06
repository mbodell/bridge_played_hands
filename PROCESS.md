## Process

The LIN file are stored individually.

Each LIN file is processed and 3 separate files are created.

1. Hand records for each board
2. List of players in the LIN file
3. Bidding/play of each hand

All the data is put into [Bridgescore+](http://www.bridgescoreplus.com).

A tournament is created in Bridgescore+ to hold all data.

Each LIN file is treated as a separate event, even though the LIN file may only contain one hand.

Each event is asked to generate statistics on the boards played in that event. These are output in CSV format.

All the CSV files are concatenated together to produce a large CSV file that is then imported into Excel.

Tools are then used to process the data in Excel.

The advantage to this approach is that it is modular. It is easy to verify the results at each stage. The final file format (Excel) is well known and queries can be generated from the results.

The modular approach means that if corrections are made to a single LIN file, then this can be processed independently of all other files.

### Hand Records

Each hand record is run through a Double Dummy Analysis (DDA) engine.
I use a customized version of 
[Bo Haglund's DDS](http://privat.bahnhof.se/wb758135/).
This generates DDA results for each denomination (NT, S, H, D, C) for each direction as well as par results.

Random checks are made on hands and the double dummy results compared against BBO's DDA engine (GiB).

### Players
A list of players for each LIN file is generated listing the LIN file number and the title of the event.

These are concatenated together to produce one big PLAYERS.txt file.

This is then sorted to create a PLAYERS_BY_NAME.txt and PLAYERS_BY_EVENT.txt file.

### Play of Hand
For each LIN file these are converted to JSON then imported to Bridgescore+.

### Data
I use this Github repository for the files.

Before I merge the repository into my 'master' files, I check to make sure that changes are reasonable.
For example, cleaning up spelling mistakes is fine, but changes to the contents of the file will be caught.

I keep a master copy of the raw LIN files and have scripts that can check for changes to the files in this repository.

Last updated:
Mon Aug 31 14:55:21 EDT 2015
