## Port settings for Plex

https://www.reddit.com/r/PleX/comments/8blaec/only_indirect_connection_to_plex_in_docker/  Find docker IP => 172.19.0.4
Find host OP => 10.82.*.* (replace * with actual numbers)  Add static route  subnet 172.19.0.0
mask 255.255.0.0 (you could also opt for 255.0.0.0 to include all 172.x.x.x nets, whatever you like)
target 10.82.*.*

route -p add 172.19.0.0 MASK 255.255.255.0 10.82.*.*


Then in Plex->Setting->Network->Custom Server Access URL add http://10.82.*.*:32400/