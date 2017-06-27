# TrackSampleState
Pair of scripts to track the state of samples as they are processed. Once they are complete fetch data

The first script fetches all samples that are in a state of running. You setup a cron job to run the script every minute.
Any sample that is running it will touch an empty file with the SID.
The second script should be setup on a cron every 5 min or so. It collects all the SID files and queries for status of those files. Once the state changes from ‘run’ to ‘succ’ it will fetch the info for the samples. At that point you can do whatever you want.  My recommendation would be to leverage a 3rd script but you could easily modify the 2nd to fetch the info for the samples and write it to a log file. Then configure rsyslog or syslogd etc.. to send the info via syslog to the SIEM. 

