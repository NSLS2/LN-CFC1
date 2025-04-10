TOP=../..

include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE
#=============================

#=============================
# Build the IOC application

PROD_IOC = ln-cfc1
# ln-cfc1.dbd will be created and installed
DBD += ln-cfc1.dbd

# ln-cfc1.dbd will be made up from these files:
ln-cfc1_DBD += base.dbd

# Include dbd files from all support applications:
ln-cfc1_DBD += menuScan.dbd
ln-cfc1_DBD += system.dbd
ln-cfc1_DBD += asyn.dbd
ln-cfc1_DBD += calcSupport.dbd
ln-cfc1_DBD += okSupport.dbd
ln-cfc1_DBD += asSupport.dbd
ln-cfc1_DBD += stdSupport.dbd
ln-cfc1_DBD += devFileWaveform.dbd
ln-cfc1_DBD += devIocStats.dbd
ln-cfc1_DBD += okSNoASub.dbd
ln-cfc1_DBD += caPutLog.dbd
ln-cfc1_DBD += reccaster.dbd

USR_CPPFLAGS += -I$(OK)  -D_X86_64_ -DUNIX -DLINUX

# Add all the support libraries needed by this IOC
ln-cfc1_LIBS += llrfapp asyn autosave devIocStats calc sscan std caPutLog seq pv reccaster pvDatabase qsrv pvaClient pvAccessIOC pvAccess pvAccessCA nt pvData

ln-cfc1_SYS_LIBS += okFrontPanel

USR_LDFLAGS += -L$(OK)

# ln-cfc1_registerRecordDeviceDriver.cpp derives from ln-cfc1.dbd
ln-cfc1_SRCS += ln-cfc1_registerRecordDeviceDriver.cpp

# Build the main IOC entry point on workstation OSs.
ln-cfc1_SRCS_DEFAULT += ln-cfc1Main.cpp
ln-cfc1_SRCS_vxWorks += -nil-

# Add support from base/src/vxWorks if needed
#ln-cfc1_OBJS_vxWorks += $(EPICS_BASE_BIN)/vxComLibrary

LIBRARY_IOC += llrfapp

llrfapp_SRCS += okiface.cpp
llrfapp_SRCS += llrfPort.cpp
llrfapp_SRCS += calc.c
llrfapp_SRCS += devFileWaveform.c
llrfapp_SRCS += devFileWaveform0.c
llrfapp_SRCS += okSNoASub.c

# Link QSRV (pvAccess Server) if available
ifdef EPICS_QSRV_MAJOR_VERSION
    ln-cfc1_LIBS += qsrv
    ln-cfc1_LIBS += $(EPICS_BASE_PVA_CORE_LIBS)
    ln-cfc1_DBD  += PVAServerRegister.dbd
    ln-cfc1_DBD  += qsrv.dbd
endif

# Finally link to the EPICS Base libraries
ln-cfc1_LIBS += $(EPICS_BASE_IOC_LIBS)

#===========================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

