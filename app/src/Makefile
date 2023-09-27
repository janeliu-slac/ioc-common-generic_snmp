TOP=../..

include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE
#=============================

#==================================================
# Build an IOC support library

# build an ioc application

PROD_IOC_Linux = snmp
# snmp.dbd will be created and installed
DBD += snmp.dbd

# snmp.dbd will be made up from these files:
snmp_DBD +=	base.dbd
snmp_DBD +=	iocAdmin.dbd
snmp_DBD +=	asSupport.dbd
snmp_DBD +=	devSnmp.dbd

# <name>_registerRecordDeviceDriver.cpp will be created from <name>.dbd
snmp_SRCS += snmp_registerRecordDeviceDriver.cpp
snmp_SRCS_DEFAULT += snmpMain.cpp

# Add locally compiled object code
#snmp_SRCS += dbSubExample.c

# Add any needed libraries
snmp_LIBS += autosave
snmp_LIBS += devIocStats
snmp_LIBS += devSnmp
snmp_LIBS += $(EPICS_BASE_IOC_LIBS)

SYS_LIBS	+= crypto

#===========================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

