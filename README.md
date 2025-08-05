# HFSLIP TOOLS

Collection of utilities used by HFSLIP. Most of these were included with and taken from HFSLIP 1.7.11u. Simply download and extract into the respective HFSLIP directories for HFSLIP to use.

I claim zero ownership of rights to the following utilities. The original authors are creditted to the best of my abilities.

Below is a list of what's included, with info, comments, and other sources of download.

\HFCABS:

- **wbemoc.cab**
  
  A specially-made wbemoc.cab file used to solve [an issue with XP SP3](https://ballzofiya.be/-/hfslip/xpsp3.html).
  
  Official download: https://ballzofiya.be/-/hfslip/

  *Thanks to Tomcat76 for hosting these sites!*

\HFTOOLS:

- **7za.exe**

  (c) Igor Pavlov
  
  Heavily-used by HFSLIP for compression and decompression tasks.
  
  Grab the latest version directly from *7zip*'s official Sourceforge page. Found in a given release's `7zXXXX-extra.7z` archive.
  
  Official download: https://sourceforge.net/projects/sevenzip/files/7-Zip/
  
- **bbie.exe** (v1.0, latest)

  (C) 2001, Bart Lagerweij
  
  Used to extract the boot image from a Windows setup disc. Works with both physical discs and ISO images. HFSLIP will use this to attempt extracting the boot image from a physical disc if there isn't already a `boot.bin` located in `\HFTOOLS`.
  
  Official archived download: https://web.archive.org/web/20120428225057/http://www.nu2.nu/bbie/

- **[2k/xp]boot.bin**
  
  (c) Microsoft
  
  The boot partitions of a Windows 2000 SP4 and Windows XP SP3 setup disc, respectively. Before running hfslip, just make a copy of the desired image file in the HFTOOLS directory and rename it to `boot.bin`. You can run `bbie.exe` with your own setup disc/ISO and create a fresh `boot.bin` image if desired.

- **CDIMAGE.exe** (v2.52)
  
  (c) 2000 / (p) 2008 (?), Microsoft
  
  The official ISO creation utility from Microsoft, included with XP SP3. It is the default choice for HFSLIP when creating the final editted ISO, with `mkisofs.exe` being chosen if `CDIMAGE.exe` is not found in `\HFTOOLS`.

- **mkisofs.exe** (v3.02a10, latest)
  
  (p) 2024, *cdrtfe* *(Requires `cygwin.ini` and `cygwin1.dll` to work.)*
  
  **mkisofs.exe[.old]** (v2.01-bootcd.ru)
  
  (c) 2004 (?), Jörg Schilling
  
  A Linux tool for ISO creation and more, there are two Windows binaries included here:
    - v2.01 provided by evgnb with HFSLIP 1.7.11u.
    - v3.02a10 from the latest v1.5.9.1 build of *cdrtfe*, a Windows disc-burning utility.
  
  IIRC I never tested `mkisofs.exe` in HFSLIP since `CDIMAGE.exe` worked just fine. If you chose to use `mkisofs.exe` over `CDIMAGE.exe`, then I'd wager the newer version would be the better choice.
  
  To get newest version of `mkisofs` from *cdrtfe*, just download the latest `.zip` archive release, and navigate to the extracted `\tools\cdrtools` folder.
  Official cdrtfe download: https://sourceforge.net/projects/cdrtfe/files/cdrtfe/

- **cmdow.exe** (v1.4.8, latest)
  
  (c) 2015, Ritchie Lawrence
  
  Used to hide the Command Prompt windows during Windows setup that execute registry edits created by HFSLIP prior. This program is seen as malicious by AVs, but this is a false-positive.
  
  The binary is inlcuded alongside the source code in the official release.
  
  Official download: https://github.com/ritchielawrence/cmdow/releases

- **modifyPE.exe** (v0.81, latest)
  
  (c) 1999, metheus
  
  Used to "[modify] file headers" according to original HFSLIP documentation, it deals with Windows checksums. Will be used by HFSLIP if ran under 2000 or XP.
  
  Official archived direct-download: https://web.archive.org/web/20150929000742/ftp://ftp.sac.sk/pub/sac/utilprog/modpe081.zip

- **PEChecksum.exe** (v1.4, latest)
  
  (c) 2008, n7Epsilon
  
  Also used to deal with Windows checksums like `modifyPE.exe`. Will be used by HFSLIP if ran under Vista or newer.
  
  Unofficial download: https://www.vogons.org/viewtopic.php?p=1021767#p1021767

- **PatchPAE3.exe** (v0.0.0.48 beta-6)
  
  (c) 2020, evgnb
  
  Provided by evgnb with HFSLIP 1.7.11u, this utility can do a whole host of things, but the three things it can do in HFSLIP is, according to evgnb:
   * "Patch SFC.dll (Win2000 with SP2+) or SFC_OS.dll (WinXP) to disable WFP if HKLM/SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\SFCSetting=0xFFFFFF9D and SfcDisable -> SFCSetting after this patch."
   * "Patch setupapi.dll in Windows 2000 [so that] Windows assume[s] HKLM\SOFTWARE\Microsoft\Driver Signing\Policy [and non-driver signing policy] == 0."
   * "Patch ntkrnlpa.exe and ntkrpamp.exe in Windows 2000 to use more than 4 Gb RAM."
  
  While the first two functions IIRC work as intended, the PAE patch is not able to be applied in my testing with either 2000's `SP4.cab` or `DRIVER.cab` file. Perhaps the Russian kernel files have a slightly different binary? Your milleage may vary.
  
  Also of note is that while they do have a GitHub page for this tool, it only has an older `v0.0.0.48 beta-3` release.
  
  Official (outdated) download: https://github.com/evgen-b/PatchPAE3/releases
  
  If anyone can find me a download link to either `beta-6` or a newer version that might hopefully have a fix for my PAE-patching issue, please let me know via a new "Issue."
