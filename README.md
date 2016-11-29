# Auto-resize-jpg-png-on-server
Auto resize JPG &amp; PNG images on a Linux system

# Installguide / Depencies
- yum install epel-release -y
- yum install optipng
- yum install jpegoptim

# Cronjob  ( every 
1. crontab -e
2. import lines:
0 2 * * 0 lockrun -Q -L .lockjpegoptim -- find /home/*/domains/*/public_html/wp-content/uploads/* -mtime -7 -iname *.jpg -exec jpegoptim --strip-all -p {} \; > /dev/null
0 3 * * 0 lockrun -Q -L .lockoptipng -- find /home/*/domains/*/public_html/wp-content/uploads/* -mtime -7 -iname *.png -exec optipng -o7 -preserve {} \; > /dev/null
