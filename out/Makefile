#
# This a Sub-Makefile of center system in DVR project,
# and used to link executable ELF file & loadable module file.
#
# Author: ROADJUN
# Creation Date: 2009-04-04
# Modifier:
# Last Modification Date:
#
#

ifeq ($(MAKELEVEL), 0)
$(error Note: This isn't a TOP Makefile)
endif

ENCODER_OBJS = 	\
		$(NVS_PATH)/acodec/wm8750.o		\
		$(NVS_PATH)/acodec/wm8751_ctrl.o		\
		$(NVS_PATH)/audio/audio.o		\
		$(NVS_PATH)/audio/BaAudioPlay.o		\
		\
		$(NVS_PATH)/video/video.o 		\
		$(NVS_PATH)/video/stream.o      	\
		\
		$(NVS_PATH)/network/ipcaudioin.o	\
		$(NVS_PATH)/network/ipcaudioout.o	\
		$(NVS_PATH)/network/ipc.o		\
		$(NVS_PATH)/network/packet.o		\
		$(NVS_PATH)/network/dhcp.o		\
		$(NVS_PATH)/network/network.o        	\
		$(NVS_PATH)/network/modeSta.o           	\
		$(NVS_PATH)/network/modeAp.o           	\
		$(NVS_PATH)/network/wpsproc.o           	\
		$(NVS_PATH)/network/yinetwork.o		\
		\
		$(NVS_PATH)/func/alarm.o		\
		$(NVS_PATH)/func/hi_draw.o		\
		$(NVS_PATH)/func/ieproc.o		\
		$(NVS_PATH)/func/main.o			\
		$(NVS_PATH)/func/moto-new.o		\
		$(NVS_PATH)/func/rs.o			\
		$(NVS_PATH)/func/authcreate.o		\
		$(NVS_PATH)/func/ieparam.o		\
		$(NVS_PATH)/func/init.o			\
		$(NVS_PATH)/func/ntp.o			\
		$(NVS_PATH)/func/netcmd.o		\
		$(NVS_PATH)/func/register.o		\
		$(NVS_PATH)/func/upnp.o				\
		$(NVS_PATH)/func/ddns.o				\
		$(NVS_PATH)/func/log.o				\
		$(NVS_PATH)/func/date.o				\
		$(NVS_PATH)/func/gpio.o				\
		$(NVS_PATH)/func/ftp.o				\
		$(NVS_PATH)/func/encrypt.o                      \
		$(NVS_PATH)/func/adpcm.o                      	\
		$(NVS_PATH)/func/sd.o                        	\
		$(NVS_PATH)/func/rs.o                           \
		$(NVS_PATH)/func/BaSysTimer.o                        	\
		$(NVS_PATH)/func/nvr.o                        	\
		$(NVS_PATH)/func/mail.o                        	\
		\
		$(NVS_PATH)/func/download.o                           \
		\
		$(NVS_PATH)/param/sysparam.o 			\
		$(NVS_PATH)/factory/dns.o			\
		$(NVS_PATH)/web/web.o \
		$(NVS_PATH)/factory/factory.o                   \
		\
		$(NVS_PATH)/func/recorder.o                           \
		$(NVS_PATH)/func/sndtools.o                           \
		$(NVS_PATH)/func/Bell.o                           \
		$(NVS_PATH)/func/Bell-on.o                           \
		$(NVS_PATH)/func/Bell-alarm.o                           \
		$(NVS_PATH)/func/Bell-press.o                           \
		$(NVS_PATH)/func/Bell-open.o                           \
		$(NVS_PATH)/func/Bell-checkio.o                        \
		$(NVS_PATH)/func/Bell-timer.o                        \
		$(NVS_PATH)/func/jPush.o                        \
		$(NVS_PATH)/func/push.o                        \

ENCODER_OBJS	+=	\
		$(NVS_PATH)/p2p/p2p.o			\

ENCODER_OBJS += 	\
		$(NVS_PATH)/i2c/i2ctest.o			\
        
NVRAM_OBJS 	= /Lib/NVRAM/libnvram-0.9.28.so
WEB_OBJS 	= /Lib/WEB/libwebs.a
#ALSA_LIB	= ~/WorkSpace/Lib/alsa-lib/lib/libasound.so.2.0.0
WPS_LIB		= /Lib/WPS/libwps.a
OBJ_LIB		= /Lib/TEST/libobj.a

LIBWIFI	= $(NVS_PATH)/vbuf/lib/libvbuf.a

.PHONY : all
all: encoder

encoder: $(ENCODER_OBJS);
	@echo "create executable file: $@ ..."
	$(CCC) -I../include -I../web -lpthread -lm -o $@ $^  $(TUTK_LIB) $(P2P_OBJS) $(NVRAM_OBJS) $(ENCRPT_LIBS) $(WEB_OBJS) $(WPS_LIB) $(OBJ_LIB)  $(SENSOR_LIB) $(LIBWIFI)
	@echo "create executable file end"
#$(ENCODER_OBJS)
	mipsel-linux-strip encoder
	cp encoder ~/tftpboot/encoder
	@echo "==================$(AP_MODULE)=================="

.PHONY : clean
clean:
	rm -f ./encoder
	rm -f ./*.a
	rm -f func/fuction.a
	rm -f func/*.o
	rm -f web/web.a
	rm -f web/*.o
	rm -f video/video.a
	rm -f video/*.o
	rm -f audio/audio.a
	rm -f audio/*.o
	rm -f acodec/wm8750.a
	rm -f acodec/*.o
	rm -f param/param.a
	rm -f param/*.o
	rm -f factory/dns.a
	rm -f factory/*.o
	rm -f video-291a/*.o
	rm -f func/moto-new.o
	rm -f $(ENCODER_OBJS)

