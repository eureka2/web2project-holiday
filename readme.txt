Holiday 0.3
CaseySoftware, LLC
webmaster@caseysoftware.com

The Holiday module uses the PEAR library for calculating holidays.  
Additionally, it features a whitelist & blacklist for adding custom holidays 
based on additional requirements, etc.  The goal is to allow for more 
advanced calculation of workhours and project dates, etc.

The original version of this module was developed by Vegard Fiksdal 
<fiksdal@sensorlink.no> of Sensorlink and acknowledged in license.txt

COMPATIBLE VERSIONS

=====================================

*  This module is being developed specifically for Web2project v2.1+.  It is 
unknown if it is compatible with any previous versions.  It is not compatible 
with any version of dotProject and no future releases will support dotProject.

KNOWN/PREVIOUS ISSUES

=====================================

From 0.2: 

*  This module was originally developed for dotProject in December 2008.

INSTALL

=====================================

1.  To install this module, please follow the standard module installation 
procedure.  Download the latest version from Sourceforge and unzip 
this directory into your web2project/modules directory.

2.  Select to System Admin -> View Modules and you should see "holiday" near 
the bottom of the list.

3.  On the "Holiday" row, select "install".  The screen should refresh.  Now 
select "hidden" and then "disabled" to make it display in your module 
navigation.


3. Open the dateclass in the editor of choise:
	vi /path/to/web2project/classes/w2p/Utilities/Date.class.php
4. Paste the following in the beginning of the isWorkingDay function (Line 148)
		if ($AppUI->isActiveModule('holiday')) {
			// Holiday module, check the holiday database
			require_once W2P_BASE_DIR."/modules/holiday/holiday_functions.class.php";
			if(HolidayFunctions::isHoliday($this)) {
				return false;
			}
		}
