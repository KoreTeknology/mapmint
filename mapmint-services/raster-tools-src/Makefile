PREFIX=/usr/local

XSLT_LDFLAGS=-L/usr/local/lib -lxslt -lxml2 -lz -liconv -lm

ZOO_FILE=/Users/djay/MapMint/zoo-project-1.5.0/trunk/zoo-project/zoo-kernel//service_internal_ms.o /Users/djay/MapMint/zoo-project-1.5.0/trunk/zoo-project/zoo-kernel//service_internal.o
ZOO_DIR=/Users/djay/MapMint/zoo-project-1.5.0/trunk/zoo-project/zoo-kernel/

ZRPATH=/Users/djay/MapMint/zoo-project-1.5.0/trunk/zoo-project/zoo-kernel//../
include ${ZRPATH}/zoo-kernel/ZOOMakefile.opts


CPPFLAGS        :=  -DZOO_SERVICE ${JSLDFLAGS} ${JS_ENABLED} ${JSCFLAGS} -DUSE_CAIRO -DUSE_KML -DUSE_MS -I${ZOO_DIR} -I${ZOO_DIR}/../../thirds/cgic206

BIN_LIST = cgi-env/service.zo


cgi-env/service.zo: service.c service1.c
	g++ -I${INST_INCLUDE} ${XML2_CPPFLAGS} ${GDAL_CFLAGS} ${MS_CFLAGS} ${CPPFLAGS} -shared -fpic $< service1.c ${XSLT_LDFLAGS} ${XML2LDFLAGS} ${MACOS_LD_NET_FLAGS} ${MS_LDFLAGS} ${GDAL_LIBS} -lc  -lcrypto  -lcurl -lfcgi ${MACOS_CFLAGS} ${MACOS_LD_FLAGS} -L${INST_LIB} -lzoo_service -o $@

install: 
	install -d ${PREFIX}/raster-tools/
	install $(BIN_LIST)             ${PREFIX}/raster-tools/
	install cgi-env/*.zcfg          ${PREFIX}/raster-tools/
	install cgi-env/*.py            ${PREFIX}/raster-tools/
	install cgi-env/*.js            ${PREFIX}/raster-tools/
	cd ${PREFIX}/raster-tools/ && ln -s ../main.cfg
	cd ${PREFIX}/raster-tools/ && ln -s ../ZOO-api.js
	cd ${PREFIX}/raster-tools/ && ln -s ../ZOO-proj4js.js


clean : 
	rm -f cgi-env/*zo

