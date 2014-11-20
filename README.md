graphite-hoverbox
=================

client side graphite frontend inspired by the hoverbox image gallery library (http://sonspring.com/journal/hoverbox-image-gallery).
The idea was to display all hosts in graphite and have the possibility to get a zoomed version as well.

requirements:
- you need a graphite server installed and the API must be available from the client browser
- CPU, memory, disk, interrupt and swap data are in the format exposed via munin-graphite bridge (can be converted to collectd with some effort)

install:

- clone and edit index.html to set graphite host and naming schema of your graphite instance (if needed) 
- in case you dont have a server installation, you need to pull the list of servers in a local json file
a json file can be generated with curl, e.g.:

	curl -k -o server-test.json "https://graphite.yourdomain.com/metrics/find/?query=path.to.*.server*&format=treejson"

In case of server installation on the graphite host, you can also fetch json directly from graphite.

Then open index.html file in browser:

file:///Users/jobauer/workspace/hoverbox/index.html?server_list=./server-test.json&from=-1day

and you should see this:

screenshot:
<img src="screenshot/graphite-hoverbox.png">

TODO:
- make graphite host configureable: currently defined within index.html
- for huge number of hosts the graphite api gets flooded: an index site + hostclass site would be usefull



