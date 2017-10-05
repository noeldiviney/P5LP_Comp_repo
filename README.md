## PSoC_5LP_repo ##

**PSoC_5LP_repo** repository hold the default.xml manifest to allow the use of Google's "repo" to manage a number of PSoC_5LP CDC Component Library repositories.  
If you are unfamiliar with repo, you can read up on it [here](http://source.android.com/source/version-control.html).  
  
The **PSoC_5LP Component Library** repositories catered for here are

  1.  thank you Michael Bey__[CharLCD_I2C_lib](https://github.com/noeldiviney/Char_I2C_lib)
  2.  thank you odissey1______[DDS24_lib](https://github.com/noeldiviney/DDS24_lib)
  3.  thank you odissey1______[DDS32_lib](https://github.com/noeldiviney/DDS32_lib)
  4.  thank you odissey1______[Encoder_lib](https://github.com/noeldiviney/Encoder_lib)
  5.  thank you odissey1______[Ext_LCD_lib](https://github.com/noeldiviney/Ext_LCD_lib)
  6.  thank you odissey1______[KIT-059_lib](https://github.com/noeldiviney/KIT-059_lib)
  7.  thank you odissey1______[QuadDec_SW_lib](https://github.com/noeldiviney/QuadDec_SW_lib)
  8.  thank you Todd Dust____[TDust_UDB_Lib](https://github.com/noeldiviney/TDust_UDB_Lib)

  TODO more components
  
### Sadly!! we have to Create a Windows 10 working environment  ###

[Cygwin install howto](http://www.mcclean-cooper.com/valentino/cygwin_install/)

I also installed apt-cyg (cygwin apt-get) and gem.  
For editing markdown files I istalled [AsciidocFX](https://github.com/asciidocfx/AsciidocFX/releases/download/v1.5.6/AsciidocFX_Windows.exe)  
There are possibly others but my memory fails me

### Download and Install Google's repo utility ###

The above libs are managed by the repo utility.
First we need to create our work environment

    $: mkdir ~/bin
    $: curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    $: chmod a+x ~/bin/repo 

Edit ~/.bash_profile and uncomment lines 32, 33 and 34 to add ~/bin to PATH

### Create the PSoC_5LP directory ###
    
    $: mkdir ~/projects/PSoC_5LP
    $: cd projects/PSoC_5LP

#### Initialise the repositories for PSoC_5LP Components ####

    $: repo init -u https://github.com/noeldiviney/PSoC_5LP_repo

#### Download the PSoC_5LP Component Libraries ####

    $: repo sync

once this has completed you should have PSoC_5LP Component Libraries in place

### Configure PSoC Creator to add the CDC Componet libraries ###

This is a Work In Progress
