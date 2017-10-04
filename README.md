## PSoC_5LP_repo ##

**PSoC_5LP_repo** repository hold the default.xml manifest to allow the use of Google's "repo" to manage a number of PSoC_5LP CDC Component Library repositories.  
If you are unfamiliar with repo, you can read up on it [here](http://source.android.com/source/version-control.html).  
  
The **PSoC_5LP Component Library** repositories catered for here are

  1.	[CharLCD_I2C_lib](https://github.com/noeldiviney/CharLCD_I2C_lib)
  2.	[CharLCD_I2C_lib](https://github.com/noeldiviney/DDS24_lib)
  3.	[CharLCD_I2C_lib](https://github.com/noeldiviney/DDS32_lib)
  4.	[CharLCD_I2C_lib](https://github.com/noeldiviney/Encoder_lib)
  5.  [CharLCD_I2C_lib](https://github.com/noeldiviney/Ext_LCD_lib)
  6.  [CharLCD_I2C_lib](https://github.com/noeldiviney/KIT-059_lib)
  7.  [CharLCD_I2C_lib](https://github.com/noeldiviney/QuadDec_SW_lib)
  8.  [CharLCD_I2C_lib](https://github.com/noeldiviney/TDust_Lib)           thank you Todd Dust

### Sadly!! we have to Create a Windows 10 working environment  ###

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
    
