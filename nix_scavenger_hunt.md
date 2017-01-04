# *nix Scavenger Hunt

Complete the following challenges using the command-line interface on your favorite
Unix or Linux operating system. You are welcome and encouraged to consult any
additional documentation online or in books.

Please add your answers/responses/text pastes to the document after each prompt.

Note: For some of the challenges you will need to reference files included with
this repository, so you will need to fork the repo into your own Github account
and then clone it to your development environment.

## The Challenges

### Navigating the Filesystem

* Get an idea of where you are in the operating system. Use the `pwd` command to find your "path to working directory"--your current location in the filesystem of your devbox. *Paste the output of the `pwd` command here:*

/Users/mdewey

* Discover more about this filesystem. Use `ls` (the "list" command)to see what is in this directory. *What directories and files do you see when you run `ls`?*

Applications			Downloads			Public
Applications (Parallels)	Library				Rocky Mountain Ruby
Desktop				Movies				RubymineProjects
Development			Music				anaconda
Documents			Pictures			node_modules

* You can use *options* to modify how a command runs. Try using `ls -alh` to see the contents of your current directory. *How are the results different when you use the `-alh` options?*

After running the command, I see 448 results, due to the 'alh' command, which breaks down to a: all, l: long listing format, h: human readable format. This exposes a number of files that are otherwise hidden by the system by default.

* The `man` ("manual") command tells you more about how any given command works. (*WARNING:* CodeAnywhere does not support the man command. You can click the following link to complete this task: http://linux.die.net/man/). Run `man` to see instructions about how to use `man`. Then use `man` to learn what the `a`, `l`, and `h` options mean when used with the `ls` command. *Write down what those options do?*

First, running just man provides me with the following, "What manual page do you want?"

Running 'man a' returns the following:  -a      Include directory entries whose names begin with a dot (.).
Running 'man l' returns the follwing:      -l      (The lowercase letter ``ell''.)  List in long format.  (See below.)  If the
             output is to a terminal, a total sum for all the file sizes is output on a
             line before the long listing.
Running 'man h' returns the following:      -h      When used with the -l option, use unit suffixes: Byte, Kilobyte, Megabyte,
             Gigabyte, Terabyte and Petabyte in order to reduce the number of digits to
             three or less using base 2 for sizes.

* Commands can also take *arguments*, which are usually the names of files or locations that you want the command to work with. Try running `ls /` to see what files are in the *root* directory of the filesystem. *What files and directories do you see listed?*

USS11MDEWEYMB:~ mdewey$ ls /
Applications			Volumes				net
Developer			bin				opt
Downloads			cores				private
Library				dev				sbin
Network				etc				tmp
Quarantine			home				usr
System				installer.failurerequests	var
Users				keybase

* A Unix filesystem has a few special shortcuts to refer to specific locations. `/` indicates the *root* of the filesystem, meaning the top-most directory in the filesystem hierarchy. Use the `cd` ("change directory") command to move to the root directory. (Hint: Use `man` to look up the `cd` command if you have any issues) *Then run `pwd` and paste the output here:*

/

* Another special shortcut in Unix is the `~` location. This indicates the *user root* directory, meaning the top-most directory in the hierarchy that comes below your user account. Use `cd` to move to `~`. *Run `pwd` and paste the response here:*

/Users/mdewey

* Change directory into the `challenge_files` directory. Use `ls` to find only the files with a `.demo` pattern. *How many files do you find?*

USS11MDEWEYMB:challenge_files mdewey$ ls *.demo
2015_special_stuff.demo		cloaked-wookie.demo		scooter-double-mamba.demo

* Use the `cd` command to move "up" one directory. *Where are you in the filesystem now?*

/Users/mdewey/Development/wats3030/wats1030-intro-to-unix

* Press the up arrow on your keyboard. *What just happened?*

The previously run command is returned to the command line.

* Press the up arrow a few more times. *What do you see?*

Pressing the up arrow will work through the history of commands I've run in this terminal session.

* Run the `history` command. *What do you see?*

Running 'history' returns all commands I've run in this session of Terminal.

### Observing the System

* Discover what account you are logged into using the `whoami` command. *What username are you currently using?*

mdewey

* Discover who else is on your system with the `who` command. *Are any other users using your system? If so, list them here:*

USS11MDEWEYMB:wats1030-intro-to-unix mdewey$ who
mdewey   console  Dec 14 11:39
mdewey   ttys000  Jan  4 14:17

* How long has your system been running? Use `uptime` to see, and *paste the result here:*

USS11MDEWEYMB:wats1030-intro-to-unix mdewey$ uptime
14:32  up 21 days,  2:55, 2 users, load averages: 1.63 1.50 1.61

* Run `ps aux` and review the results. (Hint: Use `man` to learn more about the `ps` command and options.) *How do you interpret what you see here?*

'ps' means process status, so the results that are displayed are the current processes being run by my system.

* Run `top` and review the results. (Hint: You may need to use `ctrl-c` to get out of this app.) *How do you interpret what you see here?*

Running 'top' returns the processes running on my system but sorted by what is using the most resources. This list will update as usage changes.

### Finding and Viewing Files

* Make sure you are in the `challenge_files` directory. Use the `*` wildcard to find all the files that have the word "credit" in the filename. *How many files did you find?*

2

* Use the `more` command to view one of the `credit_cards` files you just discovered. (Hint: Type `q` to quit viewing the file. Press the `spacebar` to page down. Use your keyboard arrows to move up/down.) *What is the date in the file you have viewed?*

Last updated: 01-15-2015

* Use the `find` command to search for files more effectively. Search the sub-directories under `challenge_files` to find the location of the file named `modi_laboriosam.txt`. *Where is that file located?*

./tmp/modi_laboriosam.txt

* Use the `grep` command to search for text within a file. Use `grep` on all the `.user` files in `challenge_files` to find which files contain "WA" (the abbreviation for Washington state). *How many files did you find?*

2
challenge_files/Britt-Erdman.user
challenge_files/Lissie-Strosin.user

* Use the `-r` option of `grep` to *recursively* find the text "Waldo" hidden in a file somewhere under the `challenge_files` directory. *Paste the result showing the file and line where the word "Waldo" shows up.*

challenge_files/serial-numbers/eaque_molestiae.txt:Ut est maiores quia autem. Nisi modi Waldo sed corporis sit explicabo ut est. Et est placeat ea sunt sunt consectetur sunt incidunt. Explicabo vel esse blanditiis dolorem culpa non quia.

### Pipes and Connecting Commands

* Sometimes it's useful to output the results of a command to a text file for further analysis, reference, or processing. Try running `ls > files.txt`. Notice that the file `files.txt` was created. View that file using `more`. *What do you see in the `files.txt` file?*

USS11MDEWEYMB:wats1030-intro-to-unix mdewey$ more files.txt
LICENSE
README.md
challenge_files
files.txt
nix_scavenger_hunt.md
nix_scavenger_hunt_stretch.md

* Notice that if you run `ls -alh` in the `challenge_files` directory, the files scroll by very quickly. Sometimes it would be better to get the results in a paginated format. Try running `ls -alh | more`. *Describe what you see when you run `ls -alh | more`.*

When using the 'more' command, it breaks the returned results up into groups of results that are able to be displayed on the screen. The user can then hit Enter, use up and down arrows, or the spacebar to scroll through them and see more results.

* Earlier, when you viewed the list of active processes on your devbox using `ps aux`, the list was probably really long. You can make this list more manageable by using the pipe (`|`) to filter the results of `ps` using `grep`. Run `ps aux | grep <your_username>` to see what processes are running for your specific user. *Paste the list of processes that reference your username here:*

USS11MDEWEYMB:~ mdewey$ ps aux | grep mdewey
mdewey            934   9.8  0.1  2518492   8284   ??  S    14Dec16   0:23.65 /usr/libexec/lsd
mdewey          59396   6.8  0.3  2523936  22444   ??  R     3:12PM   0:00.12 /System/Library/Frameworks/CoreServices.framework/Frameworks/Metadata.framework/Versions/A/Support/mdworker -s mdworker -c MDSImporterWorker -m com.apple.mdworker.shared
mdewey            985   5.4  0.0  2540252   3676   ??  U    14Dec16   1:44.44 /System/Library/Frameworks/ApplicationServices.framework/Frameworks/ATS.framework/Support/fontd
mdewey           1084   2.6  0.2  2586260  19180   ??  S    14Dec16  22:49.44 /System/Library/CoreServices/SystemUIServer.app/Contents/MacOS/SystemUIServer
mdewey          59395   2.0  0.3  2527656  24372   ??  R     3:12PM   0:00.13 /System/Library/Frameworks/CoreServices.framework/Frameworks/Metadata.framework/Versions/A/Support/mdworker -s mdworker -c MDSImporterWorker -m com.apple.mdworker.shared
mdewey          47736   2.0  0.4  3346880  36420   ??  S    Tue09AM   7:42.09 /Applications/Spotify.app/Contents/MacOS/Spotify
mdewey          59397   1.2  0.2  2520424  20592   ??  U     3:12PM   0:00.08 /System/Library/Frameworks/CoreServices.framework/Frameworks/Metadata.framework/Versions/A/Support/mdworker -s mdworker -c MDSImporterWorker -m com.apple.mdworker.shared
mdewey           1083   0.5  0.2  2638480  17260   ??  S    14Dec16   2:42.73 /System/Library/CoreServices/Dock.app/Contents/MacOS/Dock
mdewey          59393   0.4  0.3  2525652  26060   ??  U     3:12PM   0:00.17 /System/Library/Frameworks/CoreServices.framework/Frameworks/Metadata.framework/Versions/A/Support/mdworker -s mdworker -c MDSImporterWorker -m com.apple.mdworker.shared
mdewey          58280   0.4  2.3  3851068 192252   ??  S     2:16PM   2:48.07 /Applications/Atom.app/Contents/Frameworks/Atom Helper.app/Contents/MacOS/Atom Helper --type=renderer --no-sandbox --primordial-pipe-token=E268BD1ECE7907152D202251BC07ABF1 --lang=en-US --node-integration=true --background-color=#fff --hidden-page --enable-pinch --num-raster-threads=2 --enable-zero-copy --disable-partial-raster --enable-gpu-memory-buffer-compositor-resources --content-image-texture-target=3553,3553,3553,3553,3553,34037,3553,3553,3553,3553,3553,34037,3553,34037,34037 --video-image-texture-target=3553,3553,3553,3553,3553,34037,3553,3553,3553,3553,3553,34037,3553,34037,34037 --mojo-channel-token=82538E20F557506B481D1360B3D9E978 --mojo-application-channel-token=731384F3B7B8CFC71C88047619B40C9D --channel=58276.1.585056706
mdewey          53533   0.2  0.5  3023548  39064   ??  S     8:55AM   1:51.93 /Applications/Tweetbot.app/Contents/MacOS/Tweetbot
mdewey            116   0.1  0.3  2646428  25620   ??  Ss   14Dec16   2:26.38 /System/Library/CoreServices/loginwindow.app/Contents/MacOS/loginwindow console
mdewey          59385   0.1  0.4  2574452  35736   ??  S     3:12PM   0:00.54 /Applications/Utilities/Terminal.app/Contents/MacOS/Terminal
mdewey          54175   0.1  0.3  1013496  26772   ??  S     9:35AM   1:52.95 /Applications/Microsoft Lync.app/Contents/MacOS/Microsoft Lync
mdewey          59069   0.0  0.1  2524572  10308   ??  S     3:07PM   0:00.08 /Applications/Parallels Desktop.app/Contents/MacOS/prl_naptd proxy
mdewey          59063   0.0  0.1  2463280   5144   ??  S     3:07PM   0:00.04 /Applications/Parallels Desktop.app/Contents/MacOS/prl_event_tap
mdewey          59012   0.0  1.5  3942684 126028   ??  S     3:07PM   0:19.75 /Applications/Parallels Desktop.app/Contents/MacOS/prl_client_app
mdewey          58287   0.0  0.5  3218560  45288   ??  S     2:16PM   0:15.16 /Applications/Atom.app/Contents/Frameworks/Atom Helper.app/Contents/MacOS/Atom Helper --eval require('/Applications/Atom.app/Contents/Resources/app.asar/src/compile-cache.js').setCacheDirectory('/Users/mdewey/.atom/compile-cache');^Jrequire('/Applications/Atom.app/Contents/Resources/app.asar/src/task-bootstrap.js');
mdewey          58279   0.0  0.1  2481740   8392   ??  S     2:16PM   0:00.05 /Applications/Atom.app/Contents/Frameworks/Electron Framework.framework/Resources/crashpad_handler --database=/tmp/Atom Crashes --url=https://crashreporter.atom.io --handshake-fd=42
mdewey          58277   0.0  0.2  2712792  20420   ??  S     2:16PM   0:12.16 /Applications/Atom.app/Contents/Frameworks/Atom Helper.app/Contents/MacOS/Atom Helper --type=gpu-process --channel=58276.0.1983407854 --mojo-application-channel-token=74269821529B2275ADBEF71CD1910BF5 --no-sandbox --supports-dual-gpus=false --gpu-driver-bug-workarounds=16,21,25,36,47,50,51,55,57,65,66,72,75 --gpu-vendor-id=0x8086 --gpu-device-id=0x1626 --gpu-driver-vendor --gpu-driver-version --gpu-driver-date --gpu-active-vendor-id=0x8086 --gpu-active-device-id=0x1626
mdewey          58276   0.0  0.8  3486728  70504   ??  S     2:15PM   0:55.56 /Applications/Atom.app/Contents/MacOS/Atom
mdewey          58243   0.0  0.2  2552380  15380   ??  S     2:13PM   0:00.75 /System/Library/Image Capture/Support/Image Capture Extension.app/Contents/MacOS/Image Capture Extension
mdewey          58241   0.0  0.2  2542752  14832   ??  S     2:13PM   0:01.78 /System/Library/Image Capture/Devices/PTPCamera.app/Contents/MacOS/PTPCamera
mdewey          57688   0.0  0.1  2505472   8568   ??  S    12:28PM   0:00.06 /System/Library/PrivateFrameworks/HelpData.framework/Versions/A/Resources/helpd
mdewey          53897   0.0  0.1  2508212   7672   ??  Ss    9:32AM   0:01.32 /System/Library/SystemConfiguration/EAPOLController.bundle/Contents/Resources/eapolclient -i en0 -u 1899749644 -g 224169620
mdewey          47742   0.0  1.7  4201200 141856   ??  S    Tue09AM   4:08.23 /Applications/Spotify.app/Contents/Frameworks/Spotify Helper.app/Contents/MacOS/Spotify Helper --type=renderer --disable-pinch --primordial-pipe-token=99678A2A81E2B5ED69AC12EC8E8BBC15 --lang=en-US --lang=en-US --log-file=/Users/mdewey/Library/Logs/Spotify_debug.log --log-severity=disable --product-version=Spotify/1.0.44.100 --disable-extensions --disable-scroll-bounce --disable-spell-checking --num-raster-threads=2 --enable-zero-copy --disable-partial-raster --enable-gpu-memory-buffer-compositor-resources --content-image-texture-target=3553,3553,3553,3553,3553,34037,3553,3553,3553,3553,3553,34037,3553,34037,34037 --video-image-texture-target=3553,3553,3553,3553,3553,34037,3553,3553,3553,3553,3553,34037,3553,34037,34037 --mojo-channel-token=71A3085D82219FCA6997E9FBD740FD80 --mojo-application-channel-token=99678A2A81E2B5ED69AC12EC8E8BBC15 --channel=47736.1.544703747
mdewey          47737   0.0  0.1  2747104   5860   ??  S    Tue09AM   0:20.44 /Applications/Spotify.app/Contents/Frameworks/Spotify Helper.app/Contents/MacOS/Spotify Helper --type=gpu-process --channel=47736.0.1422212854 --mojo-application-channel-token=635C3CE99C4FE7CB16F3475899AC761B --lang=en-US --log-file=/Users/mdewey/Library/Logs/Spotify_debug.log --log-severity=disable --product-version=Spotify/1.0.44.100 --supports-dual-gpus=false --gpu-driver-bug-workarounds=18,20,29,40,48,51,52,56,58,66,67,71,73,75 --gpu-vendor-id=0x8086 --gpu-device-id=0x1626 --gpu-driver-vendor --gpu-driver-version --gpu-driver-date --gpu-active-vendor-id=0x8086 --gpu-active-device-id=0x1626 --lang=en-US --log-file=/Users/mdewey/Library/Logs/Spotify_debug.log --log-severity=disable --product-version=Spotify/1.0.44.100
mdewey          46344   0.0  0.3  4035752  29172   ??  S    Tue09AM   1:57.99 /Applications/Messages.app/Contents/MacOS/Messages
mdewey          45238   0.0  0.1  2508856   6648   ??  S    22Dec16   0:33.44 /System/Library/PrivateFrameworks/IMTransferServices.framework/IMTransferAgent.app/Contents/MacOS/IMTransferAgent
mdewey          45117   0.0  0.0  3264844   2992   ??  S    22Dec16   0:01.65 /Applications/Google Chrome.app/Contents/Versions/55.0.2883.95/Google Chrome Helper.app/Contents/MacOS/Google Chrome Helper --type=renderer --enable-features=*AutofillCreditCardSigninPromo<AutofillCreditCardSigninPromo,AutofillProfileCleanup<AutofillProfileCleanup,BlockSmallPluginContent<PluginPowerSaverTiny,DefaultEnableGpuRasterization<DefaultEnableGpuRasterization,*OverrideYouTubeFlashEmbed<Override YouTube Flash emed,*PointerEvent<PointerEvent,*PreconnectMore<PreconnectMore,*PreferHtmlOverPlugins<Html5ByDefault,SecurityWarningIconUpdate<SecurityWarningIconUpdate,SubresourceFilter<SubresourceFilter,ViewsSimplifiedFullscreenUI<ViewsSimplifiedFullscreenUI --disable-features=DocumentWriteEvaluator<DisallowFetchForDocWrittenScriptsInMainFrame,ParseHTMLOnMainThread<ParseHTMLOnMainThread,SSLPostQuantumExperiment<SSLPostQuantum --force-fieldtrials=*AppBannerTriggering/site-engagement-eager/*AutofillCreditCardSigninPromo/Default/*AutofillProfileCleanup/Enabled/*CaptivePortalInterstitial/Enabled/*ChromeChannelStable/Enabled/*ChromeSuggestionsTuning/Default/*ClientSideDetectionModel/Model0/*DataReductionProxyUseQuic/Enabled6_Zero_RTT/*DefaultEnableGpuRasterization/DefaultEnableGpuRasterization100/*DisallowFetchForDocWrittenScriptsInMainFrame/Control_20161208_Launch/*EnforceCTForProblematicRoots/disabled/*ExtensionDeveloperModeWarning/Enabled/*ExtensionInstallVerification/Enforce/*GFE/Default/*GoogleBrandedContextMenu/default/*Html5ByDefault/Default/*InstanceID/Enabled/MaterialDesignDownloads/Enabled/*OfferUploadCreditCards/Enabled/*OmniboxBundledExperimentV1/StandardR7/*ParseHTMLOnMainThread/Default/*PasswordBranding/SmartLockBrandingSavePromptOnly/*PasswordGeneration/Disabled/*PasswordManagerSettingsMigration/Enable/*PluginPowerSaverTiny/Enabled2/*PreconnectMore/Default/*QUIC/EnabledAlternativeServicesOctober/*ReportCertificateErrors/ShowAndPossiblySend/SHA1IdentityUIWarning/Enabled/SHA1ToolbarUIJanuary2016/Warning/SHA1ToolbarUIJanuary2017/Error/*SSLCommonNameMismatchHandling/Enabled/*SSLPostQuantum/disabled/*SafeBrowsingIncidentReportingService/Default/SafeBrowsingUnverifiedDownloads/DisableByParameterMostSbTypes2/*SecurityWarningIconUpdate/Enabled/*SignInPasswordPromo/Default/*SiteIsolationExtensions/Control/*StrictSecureCookies/Default/*SubresourceFilter/EnabledForPhishingSites/TranslateServerStudy/Default/*UMA-Dynamic-Uniformity-Trial/Group2/*UMA-Population-Restrict/normal/*UMA-Uniformity-Trial-1-Percent/group_45/*UMA-Uniformity-Trial-10-Percent/group_06/*UMA-Uniformity-Trial-100-Percent/group_01/*UMA-Uniformity-Trial-20-Percent/group_04/*UMA-Uniformity-Trial-5-Percent/group_12/*UMA-Uniformity-Trial-50-Percent/group_01/WebBluetoothBlacklist/BlacklistUpdate1/*WebFontsInterventionV2/Default/ --primordial-pipe-token=A960B1B6E9A1B4386D04AA489EDAC1EE --lang=en-US --extension-process --enable-webrtc-hw-h264-encoding --enable-offline-auto-reload --enable-offline-auto-reload-visible-only --blink-settings=disallowFetchForDocWrittenScriptsInMainFrame=false,disallowFetchForDocWrittenScriptsInMainFrameOnSlowConnections=false --enable-pinch --num-raster-threads=2 --enable-gpu-rasterization --enable-zero-copy --enable-gpu-memory-buffer-compositor-resources --enable-main-frame-before-activation --content-image-texture-target=0,0,3553;0,1,3553;0,2,3553;0,3,3553;0,4,3553;0,5,3553;0,6,3553;0,7,3553;0,8,3553;0,9,3553;0,10,34037;0,11,34037;0,12,34037;0,13,3553;0,14,3553;0,15,3553;1,0,3553;1,1,3553;1,2,3553;1,3,3553;1,4,3553;1,5,3553;1,6,3553;1,7,3553;1,8,3553;1,9,3553;1,10,34037;1,11,34037;1,12,34037;1,13,3553;1,14,3553;1,15,3553;2,0,3553;2,1,3553;2,2,3553;2,3,3553;2,4,3553;2,5,34037;2,6,3553;2,7,3553;2,8,3553;2,9,3553;2,10,3553;2,11,3553;2,12,34037;2,13,3553;2,14,34037;2,15,34037;3,0,3553;3,1,3553;3,2,3553;3,3,3553;3,4,3553;3,5,34037;3,6,3553;3,7,3553;3,8,3553;3,9,3553;3,10,3553;3,11,3553;3,12,34037;3,13,3553;3,14,34037;3,15,34037 --service-request-channel-token=A960B1B6E9A1B4386D04AA489EDAC1EE
mdewey          29696   0.0  0.1 556667860   7180   ??  S    19Dec16   1:23.66 /Applications/Keybase.app/Contents/SharedSupport/bin/kbfs -debug -log-file=/Users/mdewey/Library/Logs/keybase.kbfs.log -runtime-dir=/Users/mdewey/Library/Caches/Keybase /keybase
mdewey          29682   0.0  0.1 556679244  10524   ??  S    19Dec16   1:34.31 /Applications/Keybase.app/Contents/SharedSupport/bin/keybase -d --log-file=/Users/mdewey/Library/Logs/keybase.service.log service
mdewey          29672   0.0  0.0 556653892   1692   ??  S    19Dec16   0:02.22 /Applications/Keybase.app/Contents/SharedSupport/bin/updater -path-to-keybase=/Applications/Keybase.app/Contents/SharedSupport/bin/keybase
mdewey          29667   0.0  0.0  3439240   2808   ??  S    19Dec16   0:41.15 /Applications/Keybase.app/Contents/Frameworks/Keybase Helper.app/Contents/MacOS/Keybase Helper --type=renderer --no-sandbox --primordial-pipe-token=E4132CB1508E5CA407841F493E12225C --lang=en-US --node-integration=true --hidden-page --enable-pinch --num-raster-threads=2 --enable-zero-copy --disable-partial-raster --enable-gpu-memory-buffer-compositor-resources --content-image-texture-target=3553,3553,3553,3553,3553,34037,3553,3553,3553,3553,3553,34037,3553,34037,34037 --video-image-texture-target=3553,3553,3553,3553,3553,34037,3553,3553,3553,3553,3553,34037,3553,34037,34037 --mojo-channel-token=1A257970DFD80B0AE0A221381F739D82 --mojo-application-channel-token=E4132CB1508E5CA407841F493E12225C --channel=29662.2.688628788
mdewey          29666   0.0  0.0  3421344   2320   ??  S    19Dec16   0:08.16 /Applications/Keybase.app/Contents/Frameworks/Keybase Helper.app/Contents/MacOS/Keybase Helper --type=renderer --no-sandbox --primordial-pipe-token=B8C4A517F578F0130EBCB02F6F4B38E5 --lang=en-US --node-integration=true --hidden-page --enable-pinch --num-raster-threads=2 --enable-zero-copy --disable-partial-raster --enable-gpu-memory-buffer-compositor-resources --content-image-texture-target=3553,3553,3553,3553,3553,34037,3553,3553,3553,3553,3553,34037,3553,34037,34037 --video-image-texture-target=3553,3553,3553,3553,3553,34037,3553,3553,3553,3553,3553,34037,3553,34037,34037 --mojo-channel-token=D8E952147FB92736A0AEEC735A77A444 --mojo-application-channel-token=B8C4A517F578F0130EBCB02F6F4B38E5 --channel=29662.1.458099466
mdewey          29664   0.0  0.0  2713348   1744   ??  S    19Dec16   0:16.46 /Applications/Keybase.app/Contents/Frameworks/Keybase Helper.app/Contents/MacOS/Keybase Helper --type=gpu-process --channel=29662.0.213582958 --mojo-application-channel-token=8DF5CDE1EF3438D763A1AD9FA3FA74CB --no-sandbox --supports-dual-gpus=false --gpu-driver-bug-workarounds=18,20,29,40,48,51,52,56,58,66,67,71,73,75 --gpu-vendor-id=0x8086 --gpu-device-id=0x1626 --gpu-driver-vendor --gpu-driver-version --gpu-driver-date --gpu-active-vendor-id=0x8086 --gpu-active-device-id=0x1626
mdewey          29662   0.0  0.3  3895508  28316   ??  S    19Dec16   4:56.59 /Applications/Keybase.app/Contents/MacOS/Keybase
mdewey          25549   0.0  0.0  2481464    380   ??  S    19Dec16   0:00.21 /Applications/Google Chrome.app/Contents/Versions/55.0.2883.95/Google Chrome Framework.framework/Helpers/crashpad_handler --database=/Users/mdewey/Library/Application Support/Google/Chrome/Crashpad --url=https://clients2.google.com/cr/report --annotation=plat=OS X --annotation=prod=Chrome_Mac --annotation=ver=55.0.2883.95 --handshake-fd=8
mdewey          25532   0.0  0.1  2538368   8944   ??  S    19Dec16   0:07.52 /Library/Application Support/Microsoft/MAU2.0/Microsoft AutoUpdate.app/Contents/MacOS/Microsoft AU Daemon.app/Contents/MacOS/Microsoft AU Daemon -psn_0_10205627
mdewey          21329   0.0  0.1  2547032   5160   ??  U    16Dec16   0:25.24 /Applications/Caffeine.app/Contents/MacOS/Caffeine
mdewey          20776   0.0  0.0  2556592   3148   ??  S    16Dec16   0:05.98 /System/Library/PrivateFrameworks/CloudKitDaemon.framework/Support/cloudd
mdewey           6971   0.0  0.1  2583556   5732   ??  S    15Dec16   0:07.06 /System/Library/PrivateFrameworks/Noticeboard.framework/Versions/A/Resources/nbagent.app/Contents/MacOS/nbagent
mdewey           3428   0.0  0.1  2555720   8652   ??  S    14Dec16   0:53.62 /System/Library/PrivateFrameworks/SyncedDefaults.framework/Support/syncdefaultsd
mdewey           2752   0.0  0.0  2481296    560   ??  S    14Dec16   0:00.29 /usr/libexec/USBAgent
mdewey           1774   0.0  0.0  2516536   2168   ??  U    14Dec16   0:04.08 /System/Library/Frameworks/ApplicationServices.framework/Frameworks/SpeechSynthesis.framework/Resources/com.apple.speech.speechsynthesisd
mdewey           1537   0.0  0.0  2511296   1432   ??  S    14Dec16   0:01.11 /System/Library/Frameworks/InputMethodKit.framework/Resources/imklaunchagent
mdewey           1308   0.0  0.0  2582784   2720   ??  S    14Dec16   0:02.89 /System/Library/PrivateFrameworks/CommerceKit.framework/Resources/LaterAgent.app/Contents/MacOS/LaterAgent
mdewey           1291   0.0  0.2  2669800  12980   ??  S    14Dec16   0:42.39 /System/Library/Services/AppleSpell.service/Contents/MacOS/AppleSpell -psn_0_319566
mdewey           1249   0.0  0.0  2550728    324   ??  S    14Dec16   0:00.72 /System/Library/PrivateFrameworks/CommerceKit.framework/Versions/A/Resources/storelegacy
mdewey           1248   0.0  0.0  3831088   3688   ??  S    14Dec16  16:22.57 /System/Library/PrivateFrameworks/CommerceKit.framework/Versions/A/Resources/storedownloadd
mdewey           1223   0.0  0.0  2481368    652   ??  S    14Dec16   0:00.62 /System/Library/PrivateFrameworks/KerberosHelper/Helpers/DiskUnmountWatcher
mdewey           1214   0.0  0.0  2553088   1676   ??  S    14Dec16   0:00.96 /System/Library/PrivateFrameworks/CommerceKit.framework/Versions/A/Resources/storeinappd
mdewey           1169   0.0  0.1  2562872   9016   ??  S    14Dec16   0:25.59 /System/Library/PrivateFrameworks/ParsecUI.framework/Versions/A/Support/SpotlightNetHelper.app/Contents/MacOS/SpotlightNetHelper
mdewey           1165   0.0  0.0  2531928   3916   ??  U    14Dec16   0:01.67 /System/Library/PrivateFrameworks/DataDetectorsCore.framework/Versions/A/XPCServices/DataDetectorsDynamicData.xpc/Contents/MacOS/DataDetectorsDynamicData
mdewey           1148   0.0  0.1  2565096   7580   ??  S    14Dec16   0:29.97 /System/Library/PrivateFrameworks/CommerceKit.framework/Versions/A/Resources/storeassetd
mdewey           1145   0.0  0.0  2513960    400   ??  Ss   14Dec16   0:03.08 /System/Library/PrivateFrameworks/CoreWLANKit.framework/Versions/A/XPCServices/WiFiProxy.xpc/Contents/MacOS/WiFiProxy
mdewey           1140   0.0  0.3  4577864  22784   ??  S    14Dec16   3:18.79 /System/Library/CoreServices/Spotlight.app/Contents/MacOS/Spotlight
mdewey           1139   0.0  0.1  2562416   8748   ??  S    14Dec16   0:15.19 /System/Library/PrivateFrameworks/CommerceKit.framework/Versions/A/Resources/storeaccountd
mdewey           1136   0.0  0.1  2548432   7136   ??  S    14Dec16   2:56.76 /Applications/BetterSnapTool.app/Contents/MacOS/BetterSnapTool
mdewey           1118   0.0  0.0   731040   3676   ??  S    14Dec16   0:24.90 /Library/Application Support/McAfee/MSS/Applications/Menulet.app/Contents/MacOS/Menulet
mdewey           1117   0.0  0.1  2557440   4808   ??  S    14Dec16   0:11.93 /System/Library/CoreServices/diagnostics_agent
mdewey           1116   0.0  0.0  2535236   2836   ??  S    14Dec16   0:03.64 /System/Library/CoreServices/WiFiAgent.app/Contents/MacOS/WiFiAgent
mdewey           1113   0.0  0.0  2506540   1604   ??  S    14Dec16   0:28.83 /System/Library/CoreServices/cloudpaird
mdewey           1111   0.0  0.0  2483252   1608   ??  S    14Dec16   0:12.17 /Users/mdewey/Library/Application Support/Spotify/SpotifyWebHelper
mdewey           1109   0.0  0.0  2551880    596   ??  S    14Dec16   0:00.76 /System/Library/PrivateFrameworks/AskPermission.framework/Versions/A/Resources/askpermissiond
mdewey           1107   0.0  0.0   740968   2400   ??  S    14Dec16   0:05.55 /Library/Application Support/McAfee/MSS/Applications/McAfee Reporter.app/Contents/MacOS/McAfee Reporter
mdewey           1103   0.0  0.0  2513248   3308   ??  S    14Dec16   0:02.51 /System/Library/Image Capture/Support/icdd
mdewey           1101   0.0  0.1  2718480  12416   ??  S    14Dec16   0:26.02 /System/Library/CoreServices/NotificationCenter.app/Contents/MacOS/NotificationCenter
mdewey           1096   0.0  0.0  2579940   1816   ??  S    14Dec16   0:02.76 /System/Library/CoreServices/Keychain Circle Notification.app/Contents/MacOS/Keychain Circle Notification
mdewey           1094   0.0  0.0  2506568    608   ??  S    14Dec16   0:00.67 /System/Library/CoreServices/SocialPushAgent.app/Contents/MacOS/SocialPushAgent
mdewey           1089   0.0  0.0  2581680   3928   ??  Us   14Dec16   0:05.74 /System/Library/CoreServices/Dock.app/Contents/XPCServices/com.apple.dock.extra.xpc/Contents/MacOS/com.apple.dock.extra
mdewey           1085   0.0  0.4  3756120  29380   ??  S    14Dec16   1:49.66 /System/Library/CoreServices/Finder.app/Contents/MacOS/Finder
mdewey           1062   0.0  0.1  2574012   8136   ??  S    14Dec16   1:22.91 /usr/libexec/sharingd
mdewey           1061   0.0  0.0  2511924   3272   ??  S    14Dec16   1:01.17 /System/Library/PrivateFrameworks/UserActivity.framework/Agents/useractivityd
mdewey           1052   0.0  0.1  2559788   5676   ??  S    14Dec16   0:47.76 /System/Library/PrivateFrameworks/IMCore.framework/imagent.app/Contents/MacOS/imagent
mdewey           1027   0.0  0.0  2523560    496   ??  S    14Dec16   0:25.54 /System/Library/Frameworks/CoreServices.framework/Frameworks/Metadata.framework/Versions/A/Support/mdworker -s mdworker-sizing -c MDSSizingWorker -m com.apple.mdworker.sizing
mdewey           1025   0.0  0.0  2471816    344   ??  S    14Dec16   0:07.35 /System/Library/Frameworks/CoreServices.framework/Frameworks/Metadata.framework/Versions/A/Support/mdflagwriter
mdewey           1017   0.0  0.1  2517452   5128   ??  U    14Dec16   0:09.04 /System/Library/CoreServices/sharedfilelistd
mdewey            976   0.0  0.1  2531364   8068   ??  S    14Dec16   1:26.63 /System/Library/PrivateFrameworks/IDS.framework/identityservicesd.app/Contents/MacOS/identityservicesd
mdewey            942   0.0  0.0  2551756   2396   ??  S    14Dec16   0:01.99 /System/Library/PrivateFrameworks/CloudDocsDaemon.framework/Versions/A/Support/bird
mdewey            939   0.0  0.1  2509000   4900   ??  S    14Dec16   0:14.33 /usr/sbin/usernoted
mdewey            935   0.0  0.1  2549856   4440   ??  S    14Dec16   0:27.66 /System/Library/Frameworks/CoreTelephony.framework/Support/CommCenter
mdewey            933   0.0  0.0  2456048     32   ??  S    14Dec16   0:00.04 /usr/sbin/pboard
mdewey            930   0.0  0.0  2487576   4004   ??  S    14Dec16   0:54.97 /usr/sbin/distnoted agent
mdewey            928   0.0  0.0  2560000   3912   ??  S    14Dec16   0:55.31 /usr/libexec/UserEventAgent (Aqua)
mdewey          59400   0.0  0.0  2445080    804 s000  S+    3:12PM   0:00.01 grep mdewey
mdewey          59388   0.0  0.0  2454892   1576 s000  S     3:12PM   0:00.02 -bash
root            59386   0.0  0.1  2480808   6540 s000  Ss    3:12PM   0:00.06 login -pf mdewey
mdewey          59383   0.0  0.1  2515108  10392   ??  S     3:12PM   0:00.05 /System/Library/CoreServices/iconservicesagent
mdewey          59382   0.0  0.1  2485944   6216   ??  S     3:12PM   0:00.03 /usr/libexec/spindump_agent
mdewey          59374   0.0  0.1  2511128   8196   ??  S     3:12PM   0:00.05 /usr/libexec/swcd
mdewey          59371   0.0  0.1  2507072   5484   ??  S     3:12PM   0:00.05 /System/Library/CoreServices/pbs
mdewey          59351   0.0  0.2  2515368  14696   ??  S     3:10PM   0:00.10 /System/Library/Frameworks/AddressBook.framework/Versions/A/XPCServices/com.apple.AddressBook.ContactsAccountsService.xpc/Contents/MacOS/com.apple.AddressBook.ContactsAccountsService
mdewey          59350   0.0  0.1  2510232   9896   ??  S     3:10PM   0:00.13 /System/Library/PrivateFrameworks/TCC.framework/Resources/tccd
mdewey          59349   0.0  0.3  2570228  25196   ??  S     3:10PM   0:00.60 /System/Library/PrivateFrameworks/MessagesKit.framework/Resources/soagent.app/Contents/MacOS/soagent
mdewey          59344   0.0  0.0  2473180   3020   ??  S     3:09PM   0:00.17 /usr/sbin/cfprefsd agent
mdewey          59343   0.0  0.1  2480160   9628   ??  S     3:09PM   0:00.06 /usr/libexec/nsurlsessiond
mdewey          59341   0.0  0.1  2534648  11760   ??  S     3:09PM   0:00.12 /System/Library/CoreServices/AirPlayUIAgent.app/Contents/MacOS/AirPlayUIAgent --launchd
mdewey          59339   0.0  0.1  2481180   5036   ??  S     3:09PM   0:00.05 /System/Library/Frameworks/Security.framework/Versions/A/Resources/CloudKeychainProxy.bundle/Contents/MacOS/CloudKeychainProxy
mdewey          59338   0.0  0.1  2480828   5184   ??  S     3:09PM   0:00.05 /System/Library/Frameworks/Security.framework/Versions/A/Resources/IDSKeychainSyncingProxy.bundle/Contents/MacOS/IDSKeychainSyncingProxy
mdewey          59337   0.0  0.0  2507584   2664   ??  S     3:09PM   0:00.05 /usr/libexec/secd
mdewey          59330   0.0  0.1  2507516   6400   ??  S     3:09PM   0:00.11 /usr/libexec/nsurlstoraged
mdewey          59327   0.0  0.1  2510804  10212   ??  S     3:09PM   0:00.18 /System/Library/Frameworks/Accounts.framework/Versions/A/Support/accountsd
mdewey          59326   0.0  0.1  2507332  11144   ??  S     3:09PM   0:00.12 /usr/libexec/secinitd
