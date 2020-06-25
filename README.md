# Solving merge conflicts in Xcode projects

* Video: https://www.youtube.com/watch?v=fDRIK7XA5tk
* Discussion: https://developer.apple.com/forums/thread/651014

## Merging Xcode projects (FB7783835)

Whenever I work on an iOS project with multiple developers working in parallel, I tend to have to spend a lot of time manually merging Xcode project files because the 'xcodeproj' file format causes conflicts that cannot be merged automatically by common merge tools like 'git merge'.

I recorded a video showing what I mean and how I currently deal with these kind of conflicts: https://www.youtube.com/watch?v=fDRIK7XA5tk

Steps to reproduce:

* Clone https://github.com/ralfebert/ExampleXcodeGitProject  

* Merge the branches change-from-bob and change-from-alice: Both added a file to the Views group which results in a typical conflict that requires manual work.

Better tooling support for merging changes would facilitate easier collaboration on Xcode projects.

I wish Xcode would have a simpler project file format that's more concise (like the Package.swift for Swift Package Manager libraries) or a tool that could be used with 'git mergetool' that could merge such changes with a semantic unterstanding of the file format.

Current workarounds for these issues:

* Generate the Xcode project using a tool like xcodegen (https://github.com/yonaskolb/XcodeGen#xcodegen) from a simpler file format

* Use .gitattributes to treat as binary / merge: https://gist.github.com/kiero/1102043 (corrupts xcodeproj occasionally)

* git mergetool for pbxproj: https://github.com/simonwagner/mergepbx (worked perfectly for quite some time but is not updated any longer and doesn't support newer additions to the Xcode project file format)
