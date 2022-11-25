[[LINUX]]

# slstatus  
suckless status bar  
## config  
**ONLY necessary edits are mentioned**  

static const struct arg args[] = {
	/* function format          argument */
	{ cpu_perc, "cpu: %s | ",           NULL },
	{ netspeed_rx, "↓%s",         "enp37s0" },
	{ netspeed_tx, "↑%s|",       "enp37s0" },
	{ run_command, "♬%s|",        "if [ $(pactl list sinks | grep 'Stumm'|cut -d' ' -f2) = 'nein' ]; then pactl list sinks | grep '^[[:space:]]Lautstärke:' | cut -d'/' -f2; else echo 'XX'; fi" },
	{ datetime, " %s",           "%a %d %b  %H:%M" },
};
