include ../utils/Makefrag

all: download/openssl-3.5.0.tar.gz
	rm -rf temp build
	mkdir -p temp build
	cd temp && tar xvf ../download/openssl-3.5.0.tar.gz
	cd temp/openssl-3.5.0 && cat ../../0001-ohos-getauxval.diff | patch -Np1 || true
	cd temp/openssl-3.5.0 && cat ../../0001-disable-sve2.diff | patch -Np1 || true
	cd temp/openssl-3.5.0 && ./Configure linux-$(GNU_ARCH) shared no-tests --prefix=$(PREFIX) --libdir=lib --openssldir=$(PREFIX) -D__OHOS__ CC=$(CC) AR=$(AR) RANLIB=$(RANLIB)
	cd temp/openssl-3.5.0 && make -j $$(nproc)
	cd temp/openssl-3.5.0 && make install_sw -j $$(nproc) DESTDIR=$(shell pwd)/build
	mkdir -p ../sysroot
	-$(STRIP) build$(PREFIX)/lib/*.so 2>/dev/null || true
	rm -f ./build$(PREFIX)/lib/*.a
	cp -rv ./build$(PREFIX)/. ../sysroot | tee file.lst

download/openssl-3.5.0.tar.gz:
	mkdir -p download
	cd download && $(WGET) https://github.com/openssl/openssl/releases/download/openssl-3.5.0/openssl-3.5.0.tar.gz
