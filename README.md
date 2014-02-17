plex-dlna-profiles
==================

A set of DLNA client profiles for the Plex Media Server. 

I have included a set of client profiles for some TVs that I have used.

Some TVs have straight forward client profiles to properly setup a transcoding strategy. Others, like the Philips, needs a more 'hacky' solution because of a few bugs in the upnp implementation in this TV.

Philips
=======

Issues
------

* Doesn't send the proper information in the USER-AGENT when requesting a resource (i.e. movie). 
* Sends ssdp:byebye NOTIFY multicast requests after detecting a DLNA Server.
 

Resolution
----------
* Block the ssdp:byebye packets broadcasted by this TV on the DLNA Server through an iptables rule. This will allow Plex Media Server to keep the device mapping and NOT unmap it.
