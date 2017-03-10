FROM ubuntu:trusty

RUN apt-get update && apt-get upgrade && apt-get install -y build-essential checkinstall wget debhelper gcj-jdk ruby1.9 quilt
RUN gem install fpm
RUN wget https://launchpad.net/ubuntu/+archive/primary/+files/pdftk_2.02-4.debian.tar.xz
RUN wget https://launchpad.net/ubuntu/+archive/primary/+files/pdftk_2.02.orig.tar.gz
RUN tar -xzvf pdftk_2.02.orig.tar.gz
RUN tar -xvf pdftk_2.02-4.debian.tar.xz
RUN mv debian pdftk-2.02-dist
RUN cd pdftk-2.02-dist && QUILT_PATCHES=debian/patches quilt push -a
RUN cd pdftk-2.02-dist/pdftk && make -f Makefile.Debian
RUN cd pdftk-2.02-dist/pdftk && make -f Makefile.Debian install

RUN mkdir -p /fpm/usr/local/bin
RUN cp /usr/local/bin/pdftk /fpm/usr/local/bin

RUN mkdir /out
RUN ls -la /fpm

WORKDIR /fpm

CMD fpm -s dir -d "libgcc1 (>=0)" -d "libgcj14 (>=4.8)" -d "libc6 (>=2.14)" "-d libstdc++6 (>=0)" -t deb -n pdftk -v 2.02-4 usr/local/bin/pdftk && cp /fpm/*.deb /out