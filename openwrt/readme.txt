place Makefile in:
package/network/services/eoip


/etc/config/eoip

config eoip
	option name '0'			# name of zeoip interface -> here zeoip0
	option idtun '123'		# Tunnel ID
	option dst '169.254.101.30'	# peer address
	list vlan '555'			# meaningless, OpenWRT will handle zeoip0.555
	bind '192.168.1.1'		# optional local address
	dynamic '0'			# if 0 then peer is fixed with DST
