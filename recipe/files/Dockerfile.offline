# GENERATED hermetic Python runtime build (--network=none). CPython 3.15.2 is COMPILED here, offline,
# from python.org's tarball (sha256 re-checked) and the vendored build debs, by the same command the vendor
# stage ran, linked against Ubuntu's libraries; the runtime takes /usr/local from it and none of the toolchain.
FROM ubuntu:24.04@sha256:9c7f200c07e3d4a03e7249d2c16bf66a51120fb876aa2242cf31451412543289 AS cpython
ARG SOURCE_DATE_EPOCH=1795161196
ENV SOURCE_DATE_EPOCH=${SOURCE_DATE_EPOCH}
COPY vendored/python/debs/ /tmp/cpython-debs/
COPY vendored/python/Python-3.15.2.tar.xz /tmp/Python-3.15.2.tar.xz
RUN set --; for f in /tmp/cpython-debs/*.deb; do [ -e "$f" ] && set -- "$@" "$f"; done; \
    for pass in 1 2 3 4 5; do [ $# -eq 0 ] || dpkg -i --skip-same-version "$@" >/dev/null 2>&1 && break; done; \
    dpkg --configure -a && bad= && for d in "$@"; do p=$(dpkg-deb -f "$d" Package) v=$(dpkg-deb -f "$d" Version); \
      case "$(dpkg-query -W -f='${Version} ${db:Status-Abbrev}' "$p" 2>/dev/null)" in "$v ii"*) ;; *) bad="$bad $p=$v" ;; esac; done && \
    { [ -z "$bad" ] || { echo "vendored debs not installed at their vendored version:$bad" >&2; false; }; } && \
    : "${SOURCE_DATE_EPOCH:?the CPython build needs SOURCE_DATE_EPOCH}" && \
    echo "8b5536d280142ecf6cdfe15d12a21ba1c65e300bbf7b28a8d0cdb849575797de  /tmp/Python-3.15.2.tar.xz" | sha256sum -c - && \
    mkdir -p /usr/src/python && tar -xJf /tmp/Python-3.15.2.tar.xz -C /usr/src/python --strip-components=1 --no-same-owner && \
    rm -rf /tmp/cpython-debs /tmp/Python-3.15.2.tar.xz && cd /usr/src/python && \
    export DEB_BUILD_MAINT_OPTIONS=optimize=-lto && \
    PYCF="$(dpkg-buildflags --get CFLAGS) $(dpkg-buildflags --get CPPFLAGS)" && PYLD="$(dpkg-buildflags --get LDFLAGS)" && \
    ./configure --build=x86_64-linux-gnu --prefix=/usr/local --enable-shared --enable-loadable-sqlite-extensions --enable-option-checking=fatal --disable-test-modules --without-static-libpython --with-ensurepip=install --with-system-expat --without-system-libmpdec --with-dbmliborder= py_cv_module__dbm=n/a py_cv_module__gdbm=n/a py_cv_module__tkinter=n/a && \
    make -j"$(nproc)" "EXTRA_CFLAGS=$PYCF" "LDFLAGS=$PYLD,--strip-all" && \
    rm python && make -j"$(nproc)" "EXTRA_CFLAGS=$PYCF" "LDFLAGS=$PYLD,--strip-all,-rpath='\$\$ORIGIN/../lib'" python && \
    make install COMPILEALL_OPTS=--invalidation-mode=checked-hash && \
    cd / && rm -rf /usr/src/python /usr/local/lib/python3.15/idlelib /usr/local/lib/python3.15/tkinter /usr/local/lib/python3.15/turtledemo /usr/local/bin/idle3* && \
    for s in pip3 pydoc3 python3 python3-config; do ln -sfT "$s" "/usr/local/bin/${s%3*}${s#*3}"; done && \
    ldconfig && /usr/local/bin/python3 -I -B -c "import ssl, sqlite3, zlib, bz2, lzma, ctypes, uuid, pyexpat, decimal, readline, curses, hashlib, compression.zstd, sys, importlib.util as u; bad = [m for m in ('_dbm', '_gdbm', '_tkinter') if u.find_spec(m)]; assert not bad, ('built but must not be', bad); print(sys.version.replace(chr(10), ' '), '|', ssl.OPENSSL_VERSION, '| sqlite', sqlite3.sqlite_version, '| expat', pyexpat.EXPAT_VERSION)" && \
    ldd /usr/local/lib/python3.15/lib-dynload/_ssl.cpython-*.so | grep -qE 'libssl.so.3 => /(usr/)?lib/x86_64-linux-gnu/' && ldd /usr/local/lib/python3.15/lib-dynload/_sqlite3.cpython-*.so | grep -qE 'libsqlite3.so.0 => /(usr/)?lib/x86_64-linux-gnu/' && ldd /usr/local/lib/python3.15/lib-dynload/pyexpat.cpython-*.so | grep -qE 'libexpat.so.1 => /(usr/)?lib/x86_64-linux-gnu/' && ldd /usr/local/lib/python3.15/lib-dynload/_ctypes.cpython-*.so | grep -qE 'libffi.so.8 => /(usr/)?lib/x86_64-linux-gnu/' && ldd /usr/local/lib/python3.15/lib-dynload/_lzma.cpython-*.so | grep -qE 'liblzma.so.5 => /(usr/)?lib/x86_64-linux-gnu/' && ldd /usr/local/lib/python3.15/lib-dynload/_bz2.cpython-*.so | grep -qE 'libbz2.so.1.0 => /(usr/)?lib/x86_64-linux-gnu/' && ldd /usr/local/lib/python3.15/lib-dynload/_uuid.cpython-*.so | grep -qE 'libuuid.so.1 => /(usr/)?lib/x86_64-linux-gnu/' && ldd /usr/local/lib/python3.15/lib-dynload/zlib.cpython-*.so | grep -qE 'libz.so.1 => /(usr/)?lib/x86_64-linux-gnu/'
# source.pip_vendor_drop runs this script (base64 below; argv: site-packages, module, component):
#   import glob, json, os, shutil, sys
#   sp, mod, comp = sys.argv[1:4]
#   v = os.path.join(sp, "pip", "_vendor")
#   shutil.rmtree(os.path.join(v, mod))
#   rec = glob.glob(os.path.join(sp, "pip-*.dist-info", "RECORD"))[0]
#   keep = []
#   for ln in open(rec).read().splitlines(True):
#       f = ln.split(",")[0]
#       if f.startswith("pip/_vendor/" + mod + "/"):
#           continue
#       if f.startswith("pip-") and "/licenses/src/pip/_vendor/" + mod + "/" in f:
#           lic = os.path.join(sp, f)
#           if os.path.exists(lic):
#               os.remove(lic)
#           continue
#       keep.append(ln)
#   open(rec, "w").write("".join(keep))
#   vt = os.path.join(v, "vendor.txt")
#   vl = open(vt).read().splitlines(True)
#   open(vt, "w").write("".join(l for l in vl if not l.startswith(comp + "==")))
#   bp = os.path.join(v, "bom.cdx.json")
#   b = json.load(open(bp))
#   gone = {c["bom-ref"] for c in b["components"] if c["name"] == comp}
#   b["components"] = [c for c in b["components"] if c["bom-ref"] not in gone]
#   b["dependencies"] = [{**d, "dependsOn": [r for r in d["dependsOn"] if r not in gone]} if "dependsOn" in d else d
#                        for d in b["dependencies"] if d["ref"] not in gone]
#   open(bp, "w").write(json.dumps(b, indent=2, sort_keys=True) + "\n")
#   assert gone and not os.path.exists(os.path.join(v, mod)), "pip_vendor_drop: nothing was dropped"
#   assert comp not in open(bp).read() and comp + "==" not in open(vt).read()
# dep_bumps: the CVE floors, installed over the interpreter's own packages from the vendored wheels; no
# .pyc at install time (timestamped), then checked-hash .pyc in one sorted pass, as `make install` writes
COPY vendored/wheelhouse /tmp/wheelhouse
RUN PIP_DISABLE_PIP_VERSION_CHECK=1 python3 -m pip install --no-index --no-deps --no-cache-dir --no-compile --find-links /tmp/wheelhouse 'pip==26.3' && \
    python3 -c "import base64,sys; exec(base64.b64decode('CmltcG9ydCBnbG9iLCBqc29uLCBvcywgc2h1dGlsLCBzeXMKc3AsIG1vZCwgY29tcCA9IHN5cy5hcmd2WzE6NF0KdiA9IG9zLnBhdGguam9pbihzcCwgInBpcCIsICJfdmVuZG9yIikKc2h1dGlsLnJtdHJlZShvcy5wYXRoLmpvaW4odiwgbW9kKSkKcmVjID0gZ2xvYi5nbG9iKG9zLnBhdGguam9pbihzcCwgInBpcC0qLmRpc3QtaW5mbyIsICJSRUNPUkQiKSlbMF0Ka2VlcCA9IFtdCmZvciBsbiBpbiBvcGVuKHJlYykucmVhZCgpLnNwbGl0bGluZXMoVHJ1ZSk6CiAgICBmID0gbG4uc3BsaXQoIiwiKVswXQogICAgaWYgZi5zdGFydHN3aXRoKCJwaXAvX3ZlbmRvci8iICsgbW9kICsgIi8iKToKICAgICAgICBjb250aW51ZQogICAgaWYgZi5zdGFydHN3aXRoKCJwaXAtIikgYW5kICIvbGljZW5zZXMvc3JjL3BpcC9fdmVuZG9yLyIgKyBtb2QgKyAiLyIgaW4gZjoKICAgICAgICBsaWMgPSBvcy5wYXRoLmpvaW4oc3AsIGYpCiAgICAgICAgaWYgb3MucGF0aC5leGlzdHMobGljKToKICAgICAgICAgICAgb3MucmVtb3ZlKGxpYykKICAgICAgICBjb250aW51ZQogICAga2VlcC5hcHBlbmQobG4pCm9wZW4ocmVjLCAidyIpLndyaXRlKCIiLmpvaW4oa2VlcCkpCnZ0ID0gb3MucGF0aC5qb2luKHYsICJ2ZW5kb3IudHh0IikKdmwgPSBvcGVuKHZ0KS5yZWFkKCkuc3BsaXRsaW5lcyhUcnVlKQpvcGVuKHZ0LCAidyIpLndyaXRlKCIiLmpvaW4obCBmb3IgbCBpbiB2bCBpZiBub3QgbC5zdGFydHN3aXRoKGNvbXAgKyAiPT0iKSkpCmJwID0gb3MucGF0aC5qb2luKHYsICJib20uY2R4Lmpzb24iKQpiID0ganNvbi5sb2FkKG9wZW4oYnApKQpnb25lID0ge2NbImJvbS1yZWYiXSBmb3IgYyBpbiBiWyJjb21wb25lbnRzIl0gaWYgY1sibmFtZSJdID09IGNvbXB9CmJbImNvbXBvbmVudHMiXSA9IFtjIGZvciBjIGluIGJbImNvbXBvbmVudHMiXSBpZiBjWyJib20tcmVmIl0gbm90IGluIGdvbmVdCmJbImRlcGVuZGVuY2llcyJdID0gW3sqKmQsICJkZXBlbmRzT24iOiBbciBmb3IgciBpbiBkWyJkZXBlbmRzT24iXSBpZiByIG5vdCBpbiBnb25lXX0gaWYgImRlcGVuZHNPbiIgaW4gZCBlbHNlIGQKICAgICAgICAgICAgICAgICAgICAgZm9yIGQgaW4gYlsiZGVwZW5kZW5jaWVzIl0gaWYgZFsicmVmIl0gbm90IGluIGdvbmVdCm9wZW4oYnAsICJ3Iikud3JpdGUoanNvbi5kdW1wcyhiLCBpbmRlbnQ9Miwgc29ydF9rZXlzPVRydWUpICsgIlxuIikKYXNzZXJ0IGdvbmUgYW5kIG5vdCBvcy5wYXRoLmV4aXN0cyhvcy5wYXRoLmpvaW4odiwgbW9kKSksICJwaXBfdmVuZG9yX2Ryb3A6IG5vdGhpbmcgd2FzIGRyb3BwZWQiCmFzc2VydCBjb21wIG5vdCBpbiBvcGVuKGJwKS5yZWFkKCkgYW5kIGNvbXAgKyAiPT0iIG5vdCBpbiBvcGVuKHZ0KS5yZWFkKCkK').decode())" /usr/local/lib/python3.15/site-packages pkg_resources setuptools && \
    python3 -m compileall -q --invalidation-mode checked-hash /usr/local/lib/python3.15/site-packages && \
    rm -rf /tmp/wheelhouse && python3 -m pip --version
FROM ubuntu:24.04@sha256:9c7f200c07e3d4a03e7249d2c16bf66a51120fb876aa2242cf31451412543289
ENV DEBIAN_FRONTEND=noninteractive LANG=C.UTF-8 PATH=/home/python/.local/bin:/usr/local/bin:/usr/local/sbin:/usr/sbin:/usr/bin:/sbin:/bin
COPY --from=cpython /usr/local/ /usr/local/
RUN --mount=type=bind,source=vendored/debs,target=/tmp/debs \
    set --; for f in /tmp/debs/*.deb; do [ -e "$f" ] && set -- "$@" "$f"; done; \
    for pass in 1 2 3 4 5; do [ $# -eq 0 ] || dpkg -i --skip-same-version "$@" >/dev/null 2>&1 && break; done; \
    dpkg --configure -a && bad= && for d in "$@"; do p=$(dpkg-deb -f "$d" Package) v=$(dpkg-deb -f "$d" Version); \
      case "$(dpkg-query -W -f='${Version} ${db:Status-Abbrev}' "$p" 2>/dev/null)" in "$v ii"*) ;; *) bad="$bad $p=$v" ;; esac; done && \
    { [ -z "$bad" ] || { echo "vendored debs not installed at their vendored version:$bad" >&2; false; }; } && \
    ldconfig && \
    rm -rf /var/lib/apt/lists/* \
           /var/log/dpkg.log /var/log/alternatives.log /var/log/apt /var/cache/ldconfig/aux-cache /var/cache/fontconfig
ARG SOURCE_DATE_EPOCH=1795161196
RUN groupadd -r python && useradd -r -g python -d /home/python -m python && \
    : "${SOURCE_DATE_EPOCH:?SOURCE_DATE_EPOCH must be set for a reproducible build}" && \
    sed -ri "s/^([^:]*:[^:]*):[0-9]*:/\1:$((SOURCE_DATE_EPOCH/86400)):/" /etc/shadow && \
    rm -f /etc/passwd- /etc/shadow- /etc/group- /etc/gshadow-
LABEL org.opencontainers.image.licenses="Python-2.0"
LABEL org.opencontainers.image.title="Python"
LABEL org.opencontainers.image.source="https://github.com/python/cpython"
LABEL org.opencontainers.image.description="CPython 3.15.2 language runtime, built from source, non-root"
LABEL org.opencontainers.image.version="3.15.2-CE-ubuntu24.04-r5"
LABEL org.opencontainers.image.revision="5e58eaad7c58df58dfa8ea549c87996e01dd1077"
USER python
WORKDIR /home/python
ENTRYPOINT []
CMD ["python3"]
