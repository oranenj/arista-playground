An Arista vagrant lab setup using ansible provisioning

Based on the bowtie example from https://github.com/jerearista/vagrant-veos

The ansible scripts configure MLAG peering between the spines, 
though only with a single-port port-channel for the peer link,
plus the corresponding LAGs on the leaves. Traffic from one 
leaf to another should not be affected by a spine reload
