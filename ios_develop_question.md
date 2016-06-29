####1.Could not build module ‘第三方库’
Allow Non-modular Includes In Framework Modules  设置为  yes

####2.What's the difference between all the Selection Segues?
Here is a quick summary of the segues and an example for each type. You'll want to do more research/experimentation if you decide to implement them.

Show - Pushes the destination view controller onto the navigation stack, moving the source view controller out of the way (destination slides overtop from right to left), providing a back button to navigate back to the source - on all devices
Example: Navigating inboxes/folders in Mail

Show Detail - Replaces the detail/secondary view controller when in a UISplitViewController with no ability to navigate back to the previous view controller
Example: In Mail on iPad in landscape, tapping an email in the sidebar replaces the view controller on the right to show the new email

Present Modally - Presents a view controller in various different ways as defined by the Presentation option, covering up the previous view controller - most commonly used to present a view controller that animates up from the bottom and covers the entire screen on iPhone, but on iPad it's common to present it as a centered box overtop that darkens the underlying view controller and also animates up from the bottom
Example: Tapping the + button in Calendar on iPhone

Popover Presentation - When run on iPad, the destination appears in a small popover, and tapping anywhere outside of this popover will dismiss it. On iPhone, popovers are supported as well but by default if it performs a Popover Presentation segue, it will present the destination view controller modally over the full screen.
Example: Tapping the + button in Calendar on iPad (or iPhone, realizing it is converted to a full screen presentation as opposed to an actual popover)

Custom - You may implement your own custom segue and have control over its behavior.

The deprecated segues are essentially the non-adaptive equivalent of those described above. These segue types are deprecated in iOS 8: Push, Modal, Popover, Replace.

[官方文档说明链接](https://developer.apple.com/library/ios/recipes/xcode_help-interface_builder/articles-storyboard/StoryboardSegue.html)


####3.Your build settings specify a provisioning profile with the UUID, no provisioning profile was found

**两种方法：**

1)可以跳转文件到目录/users/youraccout/Library/MobileDevice/Provisioning Profiles/  移除所有的已存在的provision file. 去developer 的member center, 下载新的provision file 双击导入。在xcode中重新配置即可。 

2)1.找到项目中的**.xcodeproj文件，点击右键，show package contents(打开包内容)。
2.打开后找到project.pbxproj文件，用文本编辑器打开。其实就是右键，点击open就好了。
3.打开这个文件后，按command+F，在这个文件中查找“PROVISIONING_PROFILE",找到和这个“
PROVISIONING_PROFILE = "487F3EAC-05FB-4A2A-9EA0-31F1F35760EB";
"PROVISIONING_PROFILE[sdk=iphoneos*]" = "487F3EAC-05FB-4A2A-9EA0-31F1F35760EB";”类似的都删除。
4.然后保存文件，重新打开项目。xcode会提示你重新下载安装provisioning profile文件。下载后安装上就可以。
