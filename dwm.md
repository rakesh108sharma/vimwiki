[[LINUX]]

# dwm  
suckless window manager  

## config  
**ONLY necessary edits are mentioned**

/* appearance */
static const unsigned int borderpx  = 1;        /* border pixel of windows */
static const unsigned int snap      = 32;       /* snap pixel */
static const int showbar            = 1;        /* 0 means no bar */
static const int topbar             = 1;        /* 0 means bottom bar */
static const char *fonts[]          = { "monospace:size=15", "fontawesome:size=12" };
static const char dmenufont[]       = "monospace:size=24";


/* tagging */
static const char *tags[] = { "", "", "", "4", "5", "6", "", "8", "9" };


static const Rule rules[] = {
	/* class              instance    title       tags mask     isfloating   monitor */
	{ "Gimp",             NULL,       NULL,       0,            1,           -1 },
	{ "Firefox",          NULL,       NULL,       1 << 2,       0,           -1 },
	{ "Opera",            NULL,       NULL,       1 << 2,       0,           -1 },
	{ "Chromium",         NULL,       NULL,       1 << 1,       0,           -1 },
	{ "pavucontrol-qt",   NULL,       NULL,       1 << 6,       0,           -1 },
	{ "Tor Browser",      NULL,       NULL,       1 << 8,       0,           -1 },
	{ "Transmission-gtk", NULL,       NULL,       1 << 8,       0,           -1 },
};



/* layout(s) */
static const float mfact     = 0.55; /* factor of master area size [0.05..0.95] */

static const Layout layouts[] = {
	/* symbol     arrange function */
	{ "[M]",      monocle },
	{ "[]=",      tile },    /* first entry is default */
	{ "><>",      NULL },    /* no layout function means floating behavior */
};



/* commands */
static char dmenumon[2] = "0"; /* component of dmenucmd, manipulated in spawn() */
static const char *dmenucmd[]     = { "dmenu_run", "-i", "-m", dmenumon, "-fn", dmenufont, "-nb", col_gray1, "-nf", col_gray3, "-sb", col_cyan, "-sf", col_gray4, NULL };
static const char *btermcmd[]     = { "st", "-e", "bash",        NULL };
static const char *ztermcmd[]     = { "st", "-e", "zsh",         NULL };
static const char *qterminalcmd[] = { "qterminal", "-e", "bash", NULL };
static const char *htopcmd[]      = { "st", "-e", "htop",        NULL };
static const char *lfcmd[]        = { "st", "-e", "lf",          NULL };
static const char *viacmd[]       = { "via",                     NULL };
static const char *configcmd[]    = { "/home/maya/bin/dmconfig", NULL };
static const char *upvol[]   = { "/bin/amixer", "sset", "Master", "5%+", "unmute", NULL };
static const char *downvol[] = { "/bin/amixer", "sset", "Master", "5%-", "unmute", NULL };
static const char *mutevol[] = { "/bin/amixer", "sset", "Master", "toggle",        NULL };



static Key keys[] = {
	/* modifier                     key        function        argument */
	{ 0,              XF86XK_AudioLowerVolume, spawn,          {.v = downvol } },
	{ 0,              XF86XK_AudioMute,        spawn,          {.v = mutevol } },
	{ 0,              XF86XK_AudioRaiseVolume, spawn,          {.v = upvol   } },
	{ MODKEY,                       XK_p,      spawn,          {.v = dmenucmd } },
	{ MODKEY,                       XK_Return, spawn,          {.v = ztermcmd } },
	{ MODKEY|Mod1Mask,              XK_Return, spawn,          {.v = btermcmd } },
	{ MODKEY|ShiftMask,             XK_Return, spawn,          {.v = qterminalcmd } },
	{ MODKEY|Mod1Mask,              XK_h,      spawn,          {.v = htopcmd } },
	{ MODKEY|Mod1Mask,              XK_f,      spawn,          {.v = lfcmd } },
	{ MODKEY|Mod1Mask,              XK_c,      spawn,          {.v = configcmd } },
//	{ MODKEY|Mod1Mask,              XK_p,      spawn,          {.v = viacmd } },
