# ioc-common-generic_snmp
This is an EPICS IOC that is used at LCLS. This repo was automatically transferred to github from an internal filesystem repository via the scripts at https://github.com/pcdshub/afs_ioc_migration.

The original filesystem location was /afs/slac.stanford.edu/g/cd/swe/git/repos/package/epics/ioc/common/generic_snmp.git.


## Original readme files
### README
This is an attempt at writing a generic SNMP IOC.

Do not modify this repository directly, unless you are improving the
generic IOC.  In general, you should make a *new* repository, and push
this into it and make changes to the new repo.  The commands should be
something like:
    export GIT_TOP=/afs/slac.stanford.edu/g/cd/swe/git/repos
    git-bare-repo $GIT_TOP/package/epics/ioc/common/$(NEWREPO).git
    git clone $GIT_TOP/package/epics/ioc/common/generic_modbus.git $(LOCAL)
    cd $(LOCAL)
    git remote add new-origin $GIT_TOP/package/epics/ioc/common/$(NEWREPO).git
    git push new-origin
    git remote remove origin
    git remote rename new-origin origin

Then, you need to customize this:
    - Copy iocBoot/device-sample.cfg into app/Db/$(DEVICE).cfg, and add in the
      information for the new SNMP device.
    - Add a lines in the Makefile to install your new device:
          DB += $(DEVICE).db $(DEVICE)_mibs.db
	  ARCHIVE += $(DEVICE).archive
      (Don't actually use a symbol here!)
    - Add the appropriate MIB files into the mibs directory.
    - Copy iocBoot/ioc-sample.cfg into children/$(IOC).cfg, and configure the IOC
      to use your new device type.

