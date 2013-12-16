nobase_lib_LTLIBRARIES = opencryptoki/stdll/libpkcs11_ep11.la

opencryptoki_stdll_libpkcs11_ep11_la_LDFLAGS = -shared -Wl,-Bsymbolic	\
					     -lc -lpthread -lcrypto -lrt -llber

# Not all versions of automake observe libname_CFLAGS
opencryptoki_stdll_libpkcs11_ep11_la_CFLAGS = -DDEV -D_THREAD_SAFE            \
					    -DSHALLOW=0 -DEPSWTOK=1 -DLITE=0  \
					    -DNOCDMF -DNOMD2 -DNORIPE         \
					    -fPIC -O0 -DDEFENSIVE_MECHLIST 		    \
					    -I/usr/include -I.		    \
					    -I../../../include/pkcs11/stdll \
					    -I../../../include/pkcs11	    \
					    -I../common -DSTDLL_NAME=\"ep11tok\"

opencryptoki_stdll_libpkcs11_ep11_la_SOURCES = ../common/asn1.c		\
					     ../common/btree.c		\
					     ../common/cert.c		\
					     ../common/hwf_obj.c	\
					     ../common/dp_obj.c		\
					     ../common/data_obj.c	\
					     ../common/decr_mgr.c	\
					     ../common/dig_mgr.c	\
					     ../common/encr_mgr.c	\
					     ../common/globals.c	\
					     ../common/loadsave.c	\
					     ../common/key.c		\
					     ../common/key_mgr.c	\
                                             ../common/mech_md5.c	\
					     ../common/mech_md2.c	\
					     ../common/mech_rng.c	\
					     ../common/mech_sha.c	\
					     ../common/new_host.c	\
					     ../common/obj_mgr.c	\
					     ../common/object.c		\
					     ../common/sess_mgr.c	\
					     ../common/sign_mgr.c	\
					     ../common/template.c	\
					     ../common/p11util.c	\
					     ../common/utility.c	\
					     ../common/verify_mgr.c	\
					     ../common/log.c		\
					     ../common/mech_list.c      \
					     ../common/shared_memory.c	\
                                             ../common/attributes.c     \
                                             ../common/sw_crypt.c       \
					     ep11_specific.c

install-data-hook:
	cd $(DESTDIR)$(libdir)/opencryptoki/stdll && \
		ln -sf libpkcs11_ep11.so PKCS11_EP11.so
	$(MKDIR_P) $(DESTDIR)$(localstatedir)/lib/opencryptoki/ep11tok/TOK_OBJ
	$(CHGRP) pkcs11 $(DESTDIR)$(localstatedir)/lib/opencryptoki/ep11tok/TOK_OBJ
	$(CHGRP) pkcs11 $(DESTDIR)$(localstatedir)/lib/opencryptoki/ep11tok
	$(CHMOD) 0770 $(DESTDIR)$(localstatedir)/lib/opencryptoki/ep11tok/TOK_OBJ
	$(CHMOD) 0770 $(DESTDIR)$(localstatedir)/lib/opencryptoki/ep11tok
	$(MKDIR_P) $(DESTDIR)$(lockdir)/ep11tok
	$(CHGRP) pkcs11 $(DESTDIR)$(lockdir)/ep11tok
	$(CHMOD) 0770 $(DESTDIR)$(lockdir)/ep11tok

uninstall-hook:
	if test -d $(DESTDIR)$(libdir)/opencryptoki/stdll; then \
		cd $(DESTDIR)$(libdir)/opencryptoki/stdll && \
		rm -f PKCS11_EP11.so; fi