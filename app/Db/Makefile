TOP=../..
include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE

#----------------------------------------------------
#  Optimization of db files using dbst (DEFAULT: NO)
#DB_OPT = YES

#----------------------------------------------------
# Create and install (or just install)
# databases, templates, substitutions like this

# Built from substitution files
DB += eventDriver.db
# DB += DEVICE.db DEVICE_mibs.db

#----------------------------------------------------
# Create and install (or just install)
# Archive files, templates, substitutions like this
#
#ARCHIVE += DEVICE.archive

# Built from sub-req files

#----------------------------------------------------
# Create and install (or just install)
# Autosave request files, templates, substitutions like this
#

# Install Autosave Templates so IOC builds can find them

# Nothing to build for autosave, just install from $AUTOSAVE/db
DB_INSTALLS += $(AUTOSAVE)/db/save_restoreStatus.db
DB_INSTALLS += $(IOCADMIN)/db/iocSoft.db
DB_INSTALLS += $(IOCADMIN)/db/devIocInfo.db

IOCRELEASE_DB += iocRelease.db

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

MACRO       = /reg/g/pcds/controls/macro/expand

vpath %.cfg $(USR_VPATH) $(GENERIC_SRC_DIRS) $(COMMON_DIR)

$(COMMON_DIR)/%.db$(RAW): %.cfg ../database.template ../dbr.template ../dbw.template
	@echo "Processing $< into .db"
	csh -c "$(MACRO) -c $< ../database.template $@"

%.db$(RAW)$(DEP): %.cfg
	@$(RM) $@
	@echo "Creating dependency $@ from $<"
	@echo $(COMMONDEP_TARGET): $< ../database.template ../dbr.template ../dbw.template >> $@

$(COMMON_DIR)/%_mibs.db$(RAW): %.cfg ../mibs.template
	@echo "Processing $< into _mibs.db"
	csh -c "$(MACRO) -c $< ../mibs.template $@"

%_mibs.db$(RAW)$(DEP): %.cfg
	@$(RM) $@
	@echo "Creating dependency $@ from $<"
	@echo $(COMMONDEP_TARGET): $< ../mibs.template >> $@

$(COMMON_DIR)/%.archive$(RAW): %.cfg ../archive.template
	@echo "Processing $< into .archive"
	csh -c "$(MACRO) -c $< ../archive.template $@"

%.archive$(RAW)$(DEP): %.cfg
	@$(RM) $@
	@echo "Creating dependency $@ from $<"
	@echo $(COMMONDEP_TARGET): $< ../archive.template >> $@
