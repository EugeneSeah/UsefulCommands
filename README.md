# UsefulCommands

Git
Sync all tags:

git fetch --prune origin "+refs/tags/*:refs/tags/*"
Revert Merge:

git revert -m 1 <merge-commit>
With ‘-m 1’ we tell git to revert to the first parent of the merge commit on the master branch. -m 2 would specify to revert to the first parent on the develop branch where the merge came from initially.



Git log including reverts:

git log -p -m --full-history path/to/some/file.ext
git log sometimes doesn't show revert commits, i.e. it shows 2 less commits the commit and the revert commit, or doesn't show in between commits before the merge on one branch (ie only showing the merge commit instead of some merge commits on the requesting branch), making it hard to trace.


Android
Command to symbolise debug addresses (for osx)

/Users/eugene/Downloads/android-ndk-r16b/tom-linux-androideabi-4.9/prebuilt/darwin-x86_64/bin/arm-linux-androideabi-addr2line -C -f -e /Applications/Unity/PlaybackEngines/AndroidPlayer/Variations/mono/Development/Symbols/armeabi-v7a/libunity.sym.so
Mac
Command to temporarily increase open file limits

ulimit -n 2048

Steps to permanently increase open file limits
In Library/LaunchDaemons create a file named limit.maxfiles.plist and paste the following in (feel free to change the two numbers (which are the soft and hard limits, respectively):

limit.maxfiles.plist
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
"http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
<key>Label</key>
<string>limit.maxfiles</string>
<key>ProgramArguments</key>
<array>
<string>launchctl</string>
<string>limit</string>
<string>maxfiles</string>
<string>524288</string>
<string>524288</string>
</array>
<key>RunAtLoad</key>
<true/>
<key>ServiceIPC</key>
<false/>
</dict>
</plist>
create corresponding limit.maxproc.plist in same folder:

limit.maxproc.plist
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple/DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
<key>Label</key>
<string>limit.maxproc</string>
<key>ProgramArguments</key>
<array>
<string>launchctl</string>
<string>limit</string>
<string>maxproc</string>
<string>2048</string>
<string>2048</string>
</array>
<key>RunAtLoad</key>
<true />
<key>ServiceIPC</key>
<false />
</dict>
</plist>
Change ownership of files to wheel:

sudo chown root:wheel /Library/LaunchDaemons/limit.maxfiles.plist
sudo chown root:wheel /Library/LaunchDaemons/limit.maxproc.plist

Load settings :

sudo launchctl load -w /Library/LaunchDaemons/limit.maxfiles.plist
sudo launchctl load -w /Library/LaunchDaemons/limit.maxproc.plist

turn csrutil off :

Turn off computer or restart

Hold down Command + R

Enter console

Type following :

csrutil disable; reboot
