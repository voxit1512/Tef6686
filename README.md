  
  FOR  TEF6686_RDS_PI_check.ino:
  
  By VoXiTPro  PA7AP
  RDS PI check, There were a lof of false pi codes.
  used latest version from marsel90.

  Only correct PI code's are now transferred to tef-gtk.
  I tested some different settings the tef module has 4 errors indication.

  0 : no error; block data was received with matching data and syndrome
  1 : small error; possible 1 bit reception error detected; data is corrected
  2 : large error; theoretical correctable error detected; data is corrected
  3 : uncorrectable error; no data correction possible

  but even with a small error i did get lot of false PI codes.
  So i decided to use zero errors.

  #  
  by Eustake (marsel90)
  With this sketch it is recommended to use together with GTK-TEF6686 v1.1 https://github.com/marsel90-1/TEF-GTK_v1.1
  #
  
  FOR TEF6686AMFM.ino and TEF6686_RDS_PI_check.ino:
  
  TEF6686 lithio 1.02 patch 2.22 AM FM XDR-GTK 1.0
  by VoXiTPro
  changes: 
  all warnings are removed  (unsigned int to signed int did go wrong)
  Filters are now switchable (AUTO is max 236khz, manual you can set 311Khz)
  Stereo on/off
  Signal measurement improvements
  Keep filter (to do) and frequency settings when switching from AM to FM / FM to AM
  Settings are now from Eustake (marsel90)
  AGC is now switchable (now for FM/AM and reversed the settings) 
  Removed some settings from Eustake, FMSI stereo improvement only for tef6687 and tef6689, Softmute_mod AM only, Wavegen and I2S audio (only using internal audio)
  You can now change settings with the antenne switch ANT A = default settings, ANT B = Improved settings, ANT C = Eustake Settings
  Settings are now A,B,C from eustake. D are improved settings from prog manual.
  AGC, Deemphasis, IF+ RF+ are now in subroutines so you can set them at other moments. If you change settings the old values will be reapplied.
  IF+ RF+ works now also for AM.
  Squelch will change volume scale for AM.  if you have the right value change the define AM_VOL_SCALE too that value (now -1)
*/  
#define AM_VOL_SCALE -1
/*  
  If you have changed the above value squelch will be off again.
  Switching from AM to FM or from FM to AM filter settings are kept
  
  Special thanks to Konrad Kosmatka, author of the original version for Sony XDR-F1HD
  https://fmdx.pl/xdr-i2c/
  https://fmdx.pl/xdr-gtk/
  Thanks also to:
  - RTVDXRO his version was the base for this version https://github.com/RTVDXRO/NXP-TEF6686-Arduino-Radio
  - FMDXklaas for testing
  - ODJeetje 
  - Eustake for default and improved settings 
  and many others ...
  Tested on Arduino Nano V3.0 at 5V

Filtersettings at the moment
XDR-GTK/XDR filter index to TEF6686 filter  *=XDR-GTK
FM BW* FM BW  AM BW* AM BW
Auto   Auto          
9k      56k   1.1k   3k 
15k     56k   1.9k   3k 
17k     56k   2.2k   3k 
20k     56k   2.5k   3k 
24k     56k   2.9k   3k 
27k     56k   3.4k   3k 
32k     56k   3.9k   4k 
36k     56k   4.6k   4k 
42k     56k   5.2k   4k 
48k     56k   6.0k   6k 
55k     56k   6.9k   6k 
63k     64k   7.9k   8k 
73k     72k   9.1k   8k 
83k     84k  10.4k   8k 
90k     84k  11.3k   8k 
95k     97k  11.8k   8k 
108k   114k  13.5k   8k 
125k   133k  15.6k   8k 
142k   151k  17.8k   8k 
159k   168k  19.9k   8k 
177k   184k  22.1k   8k 
194k   200k  24.3k   8k 
211k   217k  26.4k   8k 
229k   236k  28.6k   8k 
246k   254k  30.8k   8k 
263k   287k  32.9k   8k 
281k   311k  35.1k   8k 
298k   311k  37.3k   8k 
309k   311k  38.6k   8k 

Thanks to all who helped with this piece of software and of course the orginal writer.
