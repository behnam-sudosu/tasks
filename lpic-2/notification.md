notification

wall
	wall "reboot after 5 min"
	cat file1 | wall ===>> send wall file

before login
	vim /etc/issue.net
		#################################################################
		#                   _    _           _   _                      #
		#                  / \  | | ___ _ __| |_| |                     #
		#                 / _ \ | |/ _ \ '__| __| |                     #
		#                / ___ \| |  __/ |  | |_|_|                     #
		#               /_/   \_\_|\___|_|   \__(_)                     #
		#                                                               #
		#  You are entering into a secured area! Your IP, Login Time,   #
		#   Username has been noted and has been sent to the server     #
		#                       administrator!                          #
		#   This service is restricted to authorized users only. All    #
		#            activities on this system are logged.              #
		#  Unauthorized access will be fully investigated and reported  #
		#        to the appropriate law enforcement agencies.           #
		#################################################################
	save file
	vim /etc/ssh/ssd_config
		Banner /etc/issue.net
	save file
	service sshd restart

after login
	vim /etc/motd
		###############################################################
		#                  This is a private server!                  #
		#       All connections are monitored and recorded.           #
		#  Disconnect IMMEDIATELY if you are not an authorized user!  #
		###############################################################
	save file
	




    