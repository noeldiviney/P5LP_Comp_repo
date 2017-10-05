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
For editing markdown files [AsciidocFX](https://github.com/asciidocfx/AsciidocFX/releases/download/v1.5.6/AsciidocFX_Windows.exe)  
There are possibly others but my memory fails me

### Download and Install Google's repo utility ###

The above libs are managed by the repo utility.
First we need to create our work environment

    $: mkdir ~/bin
    $: curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    $: chmod a+x ~/bin/repo 


### Create the BSP directory for YOCTO 1.7 dizzy ###
    
    $: PATH=${PATH}:~/bin
    $: mkdir yocto-dizzy
    $: cd yocto-dizzy

#### Initialise the repositories for POKY dizzy ####

    $: repo init -u https://github.com/noeldiviney/yocto-repo -b dizzy 

#### Download yocto, poky, openembedded and all BSP metadata layers ####

    $: repo sync

once this has completed you should have a complete development environment

### Build a project ie the Wanboard-quad ###
source the environment

    $: . ./setup-environment builds/Freescale/wandboard-quad

Run Bitbake

    $: bitbake fsl-image-multimedia-full


## And thats all there is to it ##
## EXCEPT!!          ##

Raspberrypi fails to build with **yocto dizzy**, so we need **yocto daisy**

### Create the BSP directory for YOCTO 1.7 daisy ###
    
    $: PATH=${PATH}:~/bin
    $: mkdir yocto-daisy
    $: cd yocto-daisy

#### Initialise the repositories for POKY daisy ####

    $: repo init -u https://github.com/noeldiviney/yocto-repo -b daisy 

#### Download yocto, poky, openembedded and all BSP metadata layers ####

    $: repo sync

once this has completed you should have a complete development environment

### Build a project ie the raspberrypi ###
source the environment

    $: . ./setup-environment builds/Raspberrypi/model-b+

Run Bitbake

    $: bitbake rpi-hwup-image
    
