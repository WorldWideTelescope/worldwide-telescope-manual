+++
title = "The Settings Menu"
description = "The Settings menu of the AAS WorldWide Telescope."
weight = 700
+++

Using the {{ui(p="Settings")}} panel and menu, you can control settings that affect
the current view, performance, and operation. Note that these settings differ
between the Web Client and the Windows Client.

![](ui_win_Settings-Panel.png)


## Constellation Lines

The {{ui(p="Constellation Lines")}} settings apply only to the [Sky](explore.md#sky)
view.

![](ui_win_Constellation-Lines.png)

Use the {{ui(p="Constellation Lines")}} pane to create your own library of
constellation figures. These are the lines that by default are shown in red,
and map out the figures that the constellations are most famous for (the W of
Cassiopeia, for example). To create your own library (which does not delete or
replace the default library) go through the following steps:

1. Click {{ui(p="Settings")}}, then click {{ui(p="New")}} in the {{ui(p="Constellation Lines")}} pane.
2. A small {{ui(p="Figure Library Name")}} pane will appear. Enter an appropriate
   name, then click {{ui(p="OK")}}.
3. The {{ui(p="Constellation Figure Editor")}} pane will open. Click on the name of
   the first constellation for which you want to create a new figure.
4. In the main view _right_ click where you want to add a point, and draw the
   new figure.
5. Select the next constellation in the {{ui(p="Constellation Figure Editor")}}, and
   repeat step 4, until you have added all the new figures.
6. Click {{ui(p="Save")}} at the lower left of the {{ui(p="Constellation Figure Editor")}} to
   save the new figures.

When you next run WorldWide Telescope, the new figure set will be available in
this pane. Notice that the default set is available too, and remains
unchanged. The {{ui(p="Edit")}} button can be used to add points for any selected
constellation, and the {{ui(p="Delete")}} button can be used to delete the entire
library. The {{ui(p="Delete")}} button in the {{ui(p="Constellation Figure Editor")}} will
delete the figure for the selected constellation.


## Experience

The {{ui(p="Experience")}} settings apply to all of the views, and contain settings
that affect mouse operation, panning and zooming, and the appearance of the
user interface.

![](ui_win_Settings-Experience.png)

* {{ui(p="Zoom Speed")}} changes the rate at which the view is zoomed when using the
  mouse wheel.
* {{ui(p="Image Quality")}} adjusts the sharpnetss of the view. This setting is not
  often apparent, except when viewing the Earth close up.
* {{ui(p="Smooth Panning")}} avoids sharp stops when releasing the mouse during
  panning.
* {{ui(p="Zoom on Mouse")}} centers zooming on the current mouse position (normally
  zooming is focused on the center of the view).
* {{ui(p="Full Web Browser")}} launches a full web browser for links rather than a web
  window.
* {{ui(p="Full Screen Tours")}} runs tours in full-screen view.
* {{ui(p="Auto Hide Tabs")}} or {{ui(p="Auto Hide Context")}} will remove the upper and lower
  panels respectively when the mouse is not over them. To return them to view
  simply move your mouse cursor over the panels.
* {{ui(p="Transparent Tabs")}} makes the panels transparent.
* {{ui(p="Reticle/Crosshairs")}} adds the crosshairs ("+") to the center of the
  viewing area.


## Network and Cache

Use the {{ui(p="Network and Cache")}} settings to control internet connection
settings. These settings apply to all views.

![](ui_Network-Cache.png)
![](ui_Manage-Data-Cache.png)

A proxy server is not used by default, and the default port used to connect to
the internet is port 80. Change these settings only if necessary.

Use {{ui(p="Manage Data Cache")}} to clear local copies of images, tours or catalogs.
Most of this data is not initially stored locally by WorldWide Telescope, and
is only downloaded when needed. Once data is downloaded it is cached, and the
cached copy is then used on subsequent requests. This is similar to how a web
browser operates. If you want to free up disk space, or ensure that the latest
data is downloaded, click {{ui(p="Purge")}} to delete the data in the cache.


## Settings Menu Entries

Click the down arrow below {{ui(p="Settings")}} to open up the menu entries.

![](ui_win_Settings-Menu-Items.png)

* {{ui(p="Check for Updates...")}} detects whether you are running the latest version
  of WorldWide Telescope.
* {{ui(p="Product Support...")}} links to the WorldWide Telescope support page.
* {{ui(p="Restore Defaults")}} restores the default settings in the {{ui(p="View")}} and
  {{ui(p="Settings")}} menus, but does not adjust the current {{ui(p="Observing Time")}}.
* {{ui(p="Advanced")}} brings up a sub-menu with options for controlling the download
  queue, displaying performance data, and more.

   ![](ui_win_Advanced-Settings-Menu.png)

  * {{ui(p="Show Download Queue")}} shows the current image tiles being downloaded.
    The queue can be stopped, started again, flushed (all items are removed
    from the queue) and cleared (all items are removed from memory). Refer
    also to the section on the
    [Network and Cache](configuration.md#network-and-cache).
  * {{ui(p="Start Queue")}} starts the download queue.
  * {{ui(p="Stop Queue")}} stops the download queue.
  * {{ui(p="Tile Loading Throttling")}} lets you set the tile loading rate in tiles
    per second (15tps, 30tps, 60tps, 120tps, Unlimited).
  * {{ui(p="Save Cache as Cabinet File...")}} exports the current cache as a .cab
    file.
  * {{ui(p="Restore Cache from Cabinet File...")}} lets you import a .cab file with
    image cache data.
  * {{ui(p="Flush Cache")}} clears the current cache.
  * {{ui(p="Show Performance Data")}} adds a few performance metrics to the title bar
    (such as frame rate).
  * {{ui(p="Master Controller")}}: refer to the
    [Multi-Monitor Cluster](configuration.md#multi-monitor-cluster) section.
  * {{ui(p="Multi-Channel Calibration")}} provides options for calibrating the output
    of multiple projectors.
  * {{ui(p="Projector Server List")}} lets you choose from available projector
    servers.
  * {{ui(p="Send Layers to Projector Servers")}} sends the current layers to the
    selected projector servers.
* {{ui(p="Controller Setup...")}} provides options for configuring MIDI controller
  devices.
* {{ui(p="Xbox Controller Setup...")}} provides options for setting up an Xbox
  controller.
* {{ui(p="Remote Access Control...")}} lets you set up WorldWide Telescope for remote
  access from another networked computer.
* {{ui(p="Select Your Language...")}} changes the language of the user interface.
* {{ui(p="Regional Data Cache...")}} enables you to enter a URL for a local data
  cache. This is handy for classes and groups. Data is downloaded only once to
  the local cache, which participants can then access. Each user will need to
  enter the URL one time. The URL is used until the setting is cleared.
  ![](shareddatacache.jpg) For more details refer to
  [Regional Data Cache](configuration.md#regional-data-cache).
