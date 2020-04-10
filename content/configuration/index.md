+++
title = "Configuration"
description = "How to configure AAS WorldWide Telescope in non-standard ways."
weight = 1100
+++

This section contains technical information on how to configure AAS WorldWide
Telescope to run in environments other than on a single desktop or laptop
client computer.


## Multi-Monitor Cluster

A straightforward example of a multi-monitor cluster is to have a single
master computer, and a matrix of slave computers each rendering a portion of
the view.

<!-- ![](uiimages/Cluster1.jpg) NOT FOUND -->

Hoag's Object - a rare ring galaxy - displayed on a 4 x 3 cluster. With a
resolution on each monitor of 1920 x 1200 the full image is 27 Megapixels.

The master computer is shown lower right.

To setup a multi-monitor cluster, go through the following procedure:

1. Setup the hardware required, with each computer installed with WorldWide
   Telescope. Each monitor is run by a single computer, so the hardware setup
   may take some time, and require some additional hardware, such as the
   support structure shown in the image above. The computers must all be
   linked to the same local network. The identification system used for a
   matrix of computers and monitors is shown in the following table (with the
   four by three matrix shown in the image above used as an example):

   | 0,0 | 1,0 | 2,0 | 3,0 |
   | 0,1 | 1,1 | **2,1** | 3,1 |
   | 0,2 | 1,2 | 2,2 | 3,2 |

1. Some of the bios settings for each of the slave computer need to be
   changed. This process is different for each make of computer - on some it
   involves pressing F2 during the startup process. This will bring up a bios
   settings menu, and make the following changes:
   1. Ensure the Ethernet card is on. For example on a Dell computer, go to
      {{ui(p="Power Management")}} and set the {{ui(p="Low Power Mode")}} setting to {{ui(p="Off")}}.
   2. Enable a remote computer to start up this one. For example on a Dell
      computer, also in {{ui(p="Power Management")}} set the {{ui(p="Remote startup")}} setting
      to {{ui(p="On")}}.
1. Turn off any screen savers on the slave computers.
1. If it is necessary to remotely edit the config.xml files, then enable
   remote login. The following links may be useful:
   * [How to use the Remote Desktop feature of Windows XP Professional](http://support.microsoft.com/kb/315328)
   * [Turn on Remote Desktop in Windows 7, 8, 10, or Vista](https://www.howtogeek.com/howto/windows-vista/turn-on-remote-desktop-in-windows-vista/)
1. For all the slave computers in the matrix create a configuration file
   (called config.xml) in the root C: folder, with the following contents:

   | XML | Description |
   | :-- | :-- |
   | **<?xml version="1.0" encoding="utf-8"?>** |
   | **<DeviceConfig>** |
   | **<Config>** |
   | **<Device** |
   | **    MonitorCountX="4"** | The number of monitors in the X axis of the matrix. |
   | **    MonitorCountY="3"** | The number of monitors in the Y axis of the matrix. |
   | **    MonitorX="2"** | The X position of the computer in the matrix. The computer (shown in bold in the table above) is shown as the example value. Note that this index starts at zero. |
   | **    MonitorY="1"** | The Y position of the computer in the matrix. Note that this index starts from zero. |
   | **    Master="False"** | Set to "**False**". |
   | **    Width="1920"** | The desired screen resolution width for the slave. |
   | **    Height="1200"** | The desired screen resolution height for the slave. |
   | **    Bezel="1.07"** | As the physical edge of the monitors must be taken into account, certain pixels will not be rendered (those that would theoretically appear behind the edges of the monitors). The Bezel factor is the ratio of the size of the monitor to the size of the screen. An estimate of 107 percent is used in this example.
   The minimum Bezel value is 1.0.
   <!-- ![](uiimages/Cluster2.jpg) NOT FOUND --> |
   | **    ConfigFile=""** | The following three entries should be present, but with empty strings as parameters. |
   | **    BlendFile=""** |
   | **    DistortionGrid="">** |
   | **</Device>** |
   | **</Config>** |
   | **</DeviceConfig>** |

1. If the WWTRemoteControl utility is _not_ being used, add WorldWide
   Telescope on the slave computers to the start up list of programs for that
   computer (this is done through the Control Panel).
1. For large clusters consider adding a proxy server to the setup, such as
   [Squid](http://www.squid-cache.org/) , to reduce the amount of traffic over
   the web.
1. Finally, on the master computer, start WorldWide Telescope, and in the
   {{ui(p="Settings > Advanced")}} menu, select {{ui(p="Master Controller")}}. From now on the
   slave computers (when they are running WorldWide Telescope) should display
   their section of the view on the master computer.

### Restrictions

* Currently the slave computers will not show text or graphic overlays when
  playing a tour.
* The slave computers will not respond to changes in the {{ui(p="View")}} or
  {{ui(p="Settings")}} menu - they will only run with the default settings.

### Single Slave Computer

If remote control from a master computer of a single slave computer is
required, then create a confix.xml file on the slave computer such as:

| **  <?xml version="1.0" encoding="utf-8" ?>
  <DeviceConfig>
     <Config>
        <Device MonitorCountX="1" MonitorCountY="1" 
                MonitorX="0" MonitorY="0" 
                Master="False" 
                Width="1600" Height="1200" 
                Bezel="1.0" 
                ConfigFile="" BlendFile="" DistortionGrid="" /> 
     </Config>
  </DeviceConfig>
** |

### Remote Starting of the Multi-Monitor Cluster

With a large cluster such as the one shown in the image in the previous
section, it is helpful to automate the startup and shutdown of all the slave
computers from the master. To do this use the **WWTRemoteControl** utility.
For this to work though, go through the following procedure:

1. On the master computer run the **WWTRemoteControl** utility program.
2. Click the {{ui(p="Node List")}} button and add the MAC Address (physical address
   component) of each slave computer to the list. To get the MAC Address of a
   computer, open up a command-prompt window and type **getmac**. The address
   that is required is under the column {{ui(p="Physical Address")}} and should be six
   pairs of hexadecimal digits separated by hyphens.
3. When the node list is complete, close that dialog and return to the main
   dialog.
4. Click {{ui(p="Wake All")}} to turn on all of the slave computers.
5. When all the slave computers have started, click {{ui(p="Launch All")}} to start
   WorldWide Telescope.
6. When WorldWide Telescope is up and running on each slave, control the view
   from the master computer.
7. Click {{ui(p="Close All")}} to finish the session and {{ui(p="Shutdown All")}} to shutdown
   the slave computers.
8. The node list is saved to the application properties for the utility, so
   the next time it is run there is no need to re-enter the node list.


## Single-Projector Planetarium

A single projector planetarium is typically a small planetarium up to around
20 feet in diameter. To see plans and instructions for building a planetarium
suitable for a small class of students, refer to
[WorldWide Telescope Planetarium](http://www.worldwidetelescope.org/docs/WorldWideTelescopePlanetarium.html).
The key to single-projector planetariums is that the output has to be warped
in such a way that it appears correct on the dome (or geodesic dome). This
warping is most noticeable in the rendering of lines (rather than spheres).
The image below shows Saturn and the Milky Way warped for a 16:9 projector.

<!-- ![](uiimages/MirrorWarping.jpg) NOT FOUND -->

Select {{ui(p="Full Dome")}} from the [View Menu Entries](#view-menu-entries) to
initiate setup for a small planetarium.

![](../viewmenu/ui_win_Full-Dome.png)

Before clicking on {{ui(p="Full Dome")}} to activate the warping, select {{ui(p="Dome
Setup")}} to provide a few basic parameters.

{{ui(p="Start Listener")}} is a toggle setting, used in
[Multi-Projector Planetariums](#multi-projector-planetarium), so leave this
unchecked.

{{ui(p="Detach Main View to Second Monitor")}} will turn the current screen blank, and
  input control is transferred to the second view (dome or second monitor).

![](domesetup.jpg)

For {{ui(p="Dome Type")}} select from the drop down list:
- {{ui(p="Fisheye")}}
- {{ui(p="Mirrordome 16:9")}}
- {{ui(p="Mirrordome 4:3")}}
- {{ui(p="<Custom Warp>")}}

The 16:9 or 4:3 numbers refer to the aspect ratio of the projector. These are
the two most common specifications, however the option to create
[Custom Warp Files](#custom-warp-files) for other curvatures is provided.

The {{ui(p="Dome Tilt")}} angle, in degrees, locates the center of interest. For the
[WorldWide Telescope Planetarium](http://www.worldwidetelescope.org/docs/WorldWideTelescopePlanetarium.html)
dome tilted at 20 degrees, the center of interest is 70 degrees. For a classic
horizontal dome enter 90 degrees, for a kiosk look-ahead type planetarium
enter 0 degrees.

Check {{ui(p="Large Textures")}} at higher resolutions, such as 1920×1080 or
1920×1200. With lower resolutions (1024×768 or 800×600) leave this unchecked
so that no down-sampling is necessary. Also note that some graphics cards will
not support large textures, and that large textures require four times the
memory and pixel processing of small textures.

A typical setup for running WorldWide Telescope in a small telescope would be
to have the software running on a laptop, with a 16:9 projector connected to
the computer using an HDMI cable. When giving presentations in the planetarium
it can be helpful to have the image present on both the dome and the laptop
screen, in order to point out objects of interest with the mouse, for example.
If this is the case then consider setting the screen resolution of the laptop
to match the aspect ratio of the projector; the following table shows some
common options:

| Screen resolution | Aspect ratio |
| :-- | :-- |
| 800×600  | 4:3 |
| 1024×768 | 4:3 |
| 1152×864 | 4:3 |
| 1280×720 | 16:9 |
| 1280×960 | 4:3 |
| 1600×1200 | 4:3 |
| 1920×1080 | 16:9 |

If the option to {{ui(p="Detach Main View to Second Monitor")}} is used then there is
no need to match screen resolution with aspect ratio. Also note that an
[Xbox Controller](#xbox-controller) can be used to navigate in WorldWide
Telescope, which can make controlling the view in the dome more comfortable.

### Custom Warp Files

Custom warp files should be used when the aspect ratio of the projector is not
16:9 or 4:3, or you are using a variant of the standard fisheye projector.

Warp files have a .data extension and can be created using a third-party tool
called _meshmapper_ tool described at the following website:

[http://paulbourke.net/dome/meshmapper/](http://paulbourke.net/dome/meshmapper/)

This website also contains a lot of interesting and useful information about
small planetariums.

## Multi-Projector Planetarium

The following section applies to the use of WorldWide Telescope in
planetariums that use multiple projectors and a blended image. Typically these
are large and commercial or university planetariums.

Projection into a large planetarium is often done using six projectors, with
each projector projecting onto an area of the dome — with special blending
done to mask the edges. The following diagram shows two common six-projector
projection layouts:

<!-- ![](uiimages/ProjectionSixA.jpg) NOT FOUND -->

There are two methods of projection that can be configured in WorldWide
Telescope, the first using P_rojection Designer_ software, the second using an
external blending system such as _Global Immersion_. One of the main
differences between the two is that blending is done by WorldWide Telescope
when using _Projection Designer_, but is usually done in dedicated hardware
when using external blending. The two methods require different parameters in
the config.xml file.

### Projection Designer Configuration

Follow this link for more detailed information on
[Projection Designer](http://orihalcon.jp/projdesigner/). Use Projection
Designer to calibrate and set blending parameters for the dome, then define
the configuration file as follows:

| XML | Description |
| :-- | :-- |
| **<?xml version="1.0" encoding="utf-8"?>** |
| **<DeviceConfig>** |
| **<Config>** |
| **<Device** |
| **    MonitorCountX="1"** | Set to **"1"**. |
| **    MonitorCountY="1"** | Set to **"1"**. |
| **    MonitorX="1"** | Set to **"1"**. |
| **    MonitorY="1"** | Set to **"1"**. |
| **    Master="False"** | Set to "**False**". |
| **    Width="1"** | Set to **"1"**. |
| **    Height="1"** | Set to **"1"**. |
| **    Bezel="1.0"** | Set to **"1.0"**. |
| **    MultiChannelDome="True"** | Set to "**True**". |
| **    DomeTilt="20"** | Tilt of the point of focus above the spring line of the dome, in degrees. |
| **    ConfigFile="path\configfile"** | The path to the Projection Designer configuration file. Refer to Projection Designer documentation for the format and purpose of the files. |
| **    BlendFile="path\blendfile"** | The path to the Projection Designer blend file. |
| **    DistortionGrid="path\distortiongrid">** | The path to the Projection Designer distortion grid. |
| **</Device>** |
| **</Config>** |
| **</DeviceConfig>** |

### External Blending Configuration

Follow this link for more detailed information on
[Global Immersion](http://www.globalimmersion.com/Default.asp).

Define the configuration file as follows:

| XML | Description |
| :-- | :-- |
| **<?xml version="1.0" encoding="utf-8"?>** |
| **<DeviceConfig>** |
| **<Config>** |
| **<Device** |
| **    MonitorCountX="1"** | Set to **"1"**. |
| **    MonitorCountY="1"** | Set to **"1"**. |
| **    MonitorX="1"** | Set to **"1"**. |
| **    MonitorY="1"** | Set to **"1"**. |
| **    Master="False"** | Set to "**False**" |
| **    Width="1"** | Set to **"1"**. |
| **    Height="1"** | Set to **"1"**. |
| **    Bezel="1.07"** | Set to **"1.0"**. |
| **    ConfigFile=""** | The following three entries should be present, but with empty strings as parameters. |
| **    BlendFile=""** |
| **    DistortionGrid=""** |
| **    MultiChannelDome="True"** | Set to "**True**". |
| **    Heading="0"** | The left-right rotation of the projection, in degrees. |
| **    Pitch="0"** | The up-down rotation of the projection, in degrees. |
| **    Roll="0"** | The rotate-left, rotate-right rotation of the projection, in degrees. |
| **    UpFov="0"** | The field of view up from the center point, in degrees. |
| **    DownFov="0"** | The field of view down from the center point, in degrees. |
| **    DomeTilt="20"** | Tilt of the point of focus above the spring line of the dome, in degrees. |
| **    Aspect="1.390531">** | Aspect ratio of the projection, the ratio of width/height. |
| **</Device>** |
| **</Config>** |
| **</DeviceConfig>** |
