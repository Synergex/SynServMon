Name:           SynServMon

Author:         Jerry Fawcett, Senior Developer Support Engineer

Description:    A Windows service that use Synergy synxfpng utility
		to monitor Synergy service(s).

		This service will send an email when the service is not 
		detected as running and when the host specified is not found


Requirements:    Visual Studio 2015 and Synergy 10.3.1 (due to Visual Studio
		 2015) or higher. Note support for Service project type added
		 in 9.5.3 


NOTES:		Create a file named synsrvmon.ddf with servers and their ports to monitor.
		The file must be in the location set to by the logical SSM.  Note, as this
		logical will be used by a Windows service it must be set at the system level
		The file must have entries in the format - server|port.  For example,

		myxfServer|2330

		The file is read on service start, therefore, if changes to this file
		are made the service must be stopped and restarted.

		Also, if desired the email subjects and messages may be modified.  See 
		the comments that start with Customize. 

		After building install the service with the below - 

		Open a Visual Studio command prompt as Administrator (installing the service
		will not be successful unless the command prompt is opened as Administrator)
		Navigate to the folder with the service executable and run InstallUtil.exe
		passing the service executable -
			
			installutil.exe SynServMon.exe

		After the service is successfully installed then be sure to start it with the
		Services applet in the Control Panel -
		Control Panel -> Administrative Tools -> Services
