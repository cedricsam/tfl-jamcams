# Transport for London webcams scraper

Scraper for webcams in London. Based off of a similar project for [Hong Kong](https://github.com/cedricsam/tdcctv).

## List of webcams

A list of webcams as of September 2022 is check in on the project (`tfl-camera-list.txt`), that we extracted from the TfL’s XML list.

You may get an updated list of webcams from the [TfL site](https://content.tfl.gov.uk/camera-list.xml). Create a simple text file named tfl-cameras-list.txt with a webcam snapshot file per row.

```
curl "https://s3-eu-west-1.amazonaws.com/jamcams.tfl.gov.uk/" -o camera-list.xml
grep -Eo "<Key>[0-9\.]+.(mp4|jpg)</Key>" camera-list.xml | grep -Eo "[0-9\.]+.(mp4|jpg)" > tfl-camera-list.txt
```

## Run with a cron job

Run every minute, to get as much data as possible (the script may check for dups):

```
* * * * *   cd ${MYDIR}; ./getall.sh
```
