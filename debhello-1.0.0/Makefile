all:
	gcc src/hello_world.c -o src/hello_world
clean:
	rm -rf src/hello_world
install:
	/usr/bin/install -D src/hello_world ${DESTDIR}/usr/local/bin/hello_world
uninstall:
	rm -rf ${DESTDIR}/usr/local/bin/hello_world
