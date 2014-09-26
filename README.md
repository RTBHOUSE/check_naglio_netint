check_naglio_netint
===================

Another nagios plugin to check counters on intefaces via SNMP



####  INFORMATION ABOUT THIS PLUGIN ####

This plugins gets 64 bit counters from device via SNMP, calculate rates
and use power of naglio to check them. 

Plugin returns stats variables as perfomance data for further nagios 2.0
post-processing, it was testet witch graphios. ( number of data change dinamicly
as sytem change, so write in to rrd file is inefficient  )

This program is based on check_redis.pl by William Leibzon - william(at)leibzon.org

####  SETUP NOTES ####

###  Example of Usage command-line use ####

Generate performace data to graphite via garphios plugin ( also show all possible variables) 

    check_naglio_netint.pl -t 30 -H <IP> -l <USENAME> -x <authPassword> -X <privPassword> -L <authProtocol>,<privProtocol> -A    


Check if there are error increase of any of the interfaces, ar is there any of the interfaces saturate:

    check_naglio_netint.pl -t 30 -H <IP> -l <USENAME> -x <authPassword> -X <privPassword> -L <authProtocol>,<privProtocol> -A \
          -o 'PATTERN:.*discard_rate_ps,WARN:>0,CRIT:>5' \
          -o 'PATTERN:.*error_rate_ps,WARN:>0,CRIT:>5' \
          -o 'PATTERN:.*octet_64_rate_bps,WARN:>850000000,CRIT:>950000000' \
          -o 'PATTERN:.*multicast_64_rate_ps,WARN:>1000,CRIT:>10000' \
          -o 'PATTERN:.*broadcast_64_rate_ps,WARN:>1000,CRIT:>10000' \
          -o 'PATTERN:.*ucast_64_rate_ps,WARN:>65000,CRIT:>75000'





