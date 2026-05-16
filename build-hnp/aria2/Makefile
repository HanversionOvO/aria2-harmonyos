include ../utils/Makefrag

SOURCE_URL = https://github.com/aria2/aria2/releases/download/release-1.37.0/aria2-1.37.0.tar.gz
SOURCE_FILE = aria2-1.37.0.tar.gz
SOURCE_DIR = aria2-1.37.0
CONFIG_ARGS = --prefix=$(PREFIX) --host=$(GNU_ARCH)-unknown-linux-musl --disable-nls --with-openssl --enable-libaria2 --with-ca-bundle=/etc/ssl/certs/cacert.pem

$(eval $(call define_autotools_package))
