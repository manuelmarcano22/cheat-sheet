#General Purpose Cheat sheet 

A collection of things I found useful and don't wont want to forget

## Table of Contents
 - [Terminal Useful Commands](#terminal-commands)
  - [XRandr](#xrandr)
  - [Screen shots](#screen-shots)
  - [DNS](#update-dns-server)
  - [grep](#grep)
  - [Netcat](#netcat)
  - [Simple Timer](#timer)
  - [Audio](#audio)
     - [Blueetooth](#bluetooth)

 - [Programming](#programming)
    - [Markdown](#markdown)
    - [LaTeX](#latex)
    - [Python](#python)
     - [Python Resources](#python-resources)
     - [Python Commands](#python-commands)
          - [Python Talks](#python-talks)
       

## Terminal Commands
### XRandr

To connect to a HDMI screen use `xrandr --output HDMI1 --auto` then replace auto with `--left-of eDP1` or other option.

> **Tip:** can use lxrandr for quick setup. It is a lightweight GTK+2 interface for XRandR for LXDE desktop.


### Screen shots

To take a screen shot can use the command from *ImageMagick* `import`. 

### Update DNS Server

First to see the current ones do:
`cat /etc/resolv.conf`

To update modify the file */etc/resolvconf/resolv.conf.d/head*. Then can do 
`sudo service  resolvconf restart`


### grep

To delete all but one file

`ls | grep -v filename | xargs rm`

or with the extended Globbing:

`!(pattern)`


### Netcat

To start a really simple chat over lan.

`nc -l 8080`

In the other pc:

`nc $((IPComputer1)) 8080`

### Timer

```bash
$ sleep 20m; espeak -v es Yaaaa; notify-send -u critical Yaaaaaaaaa
```
And to know the running time in case you need to cancel it:

```bash
$ ps -eo '%t %c' | grep sleep
```
To monitor it every second:

```bash
$ watch -n 1 "ps -eo '%t %c' | grep sleep"
```
I put this in a function in my .bashrc

```bash
function simpletimer {
if [ $2 = 'm' ]; then 
	 stimes=`echo $1'*60' | bc -l`
else 
	stimes=`echo $1`
fi
echo 'export stimes='$stimes > ~/.timervariables
sleep $1$2 ; espeak -v en "Niggaaa, whaaaat?" ; notify-send -u critical Yaaaaaaaaaaaaaaaaaaaaa
}


function seetimer {
source ~/.timervariables
leftt=1
while [ $leftt -ne '0' ]; do
		printf -v maxbar '%s' $((COLUMNS-50))
		leftt=`ps -eo '%t %c' | grep sleep | grep -oh '[0-9][0-9]:[0-9][0-9]' | awk -F: '{print $1*60+$2}'`
		percenttimer=`echo '('$leftt/$stimes'*100)' | bc -l`
		leftt=$(($stimes-$leftt))
		printf -v percenttimer '%.2f' $percenttimer
		printf -v hashes '%0.f' `echo '(('$percenttimer'/100))*'$maxbar | bc -l`     
#		hashes=`echo $percenttimer | awk '{print int($1)}'`
		printf -v spaces '%*s' $hashes ''
		printf -v spacesleft '%*s' $(($maxbar-$hashes)) ''
		echo -ne 'Percentage: '$percenttimer' % Time left: '`date -u -d @$leftt +%T`' ['`printf '%s' ${spaces// /#}``printf '%s' ${spacesleft// /-}`']\r'
		#Where maxbar replaces * for the string length in printf. Then substitute the '' for # or -.
		sleep 1
done
}
```

### Audio

#### Bluetooth

To connect the JBL bluetooth speaker can use the  GTK+ Bluetooth Manager called [Blueman](https://github.com/blueman-project/blueman). 

After that to make the bluetooth device the output use 

`pacmd set-default-sink bluez_sink.00_1D_DF_F6_A2_66.a2dp` 

where pacmd *bluez_sink.00_1D_DF_F6_A2_66.a2dp* is my bluetooh speaker.


##Programming

### Markdown 

The simplest way to see a md file using the terminal is converting to html with pandoc and seeing it with lynx:

`pandoc file.md | lynx -stdin`



### LaTeX

A great tool to use is latexmk. with the option `-pdf -pvc` it will compile each time you change the .tex file.


###Python

#### Python Commands

To set a Simple Web Server:

`python -m SimpleHTTPServer 8888 &`


#### Python Resources

##### Python Talks
| Title | Link |
| ----- | ---- |
| PyCon 2015 Tutorials | https://www.youtube.com/playlist?list=PLx_MamJPwgQMaaFaLufNeSUJRSaq0COyO |
