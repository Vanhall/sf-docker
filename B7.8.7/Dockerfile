FROM alpine as base
RUN  apk add wget

FROM scratch
COPY --from=base /lib/x86_64-linux-gnu/libpcre2-8.so.0 \
    /lib/x86_64-linux-gnu/libuuid.so.1 \
    /lib/x86_64-linux-gnu/libidn2.so.0 \
    /lib/x86_64-linux-gnu/libssl.so.3 \
    /lib/x86_64-linux-gnu/libcrypto.so.3\
    /lib/x86_64-linux-gnu/libz.so.1 \
    /lib/x86_64-linux-gnu/libpsl.so.5 \
    /lib/x86_64-linux-gnu/libc.so.6 \
    /lib/x86_64-linux-gnu/libunistring.so.2 \
    /lib/x86_64-linux-gnu/
COPY --from=base /lib64/ld-linux-x86-64.so.2 /lib64/
COPY --from=base /bin/sh /bin/wget /bin/
COPY app.sh /opt/myapp/
WORKDIR /opt/myapp
ENTRYPOINT [ "/opt/myapp/app.sh" ]
