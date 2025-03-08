# Compilation de s6-networking sous ubuntu


https://github.com/skarnet/skalibs
https://github.com/skarnet/execline
https://github.com/skarnet/s6-dns/
https://github.com/skarnet/s6/
https://github.com/skarnet/s6-networking/


https://github.com/skarnet/s6-networking/blob/main/INSTALL



  - A POSIX-compliant C development environment
  - GNU make version 3.81 or later
  - skalibs version 2.14.3.0 or later: https://skarnet.org/software/skalibs/
  - Optional (but recommended): execline version 2.9.6.1 or later: https://skarnet.org/software/execline/
  - s6 version 2.13.1.0 or later: https://skarnet.org/software/s6/
  - s6-dns version 2.4.0.0 or later: https://skarnet.org/software/s6-dns/

  ./configure && make && sudo make install

 will work for most users.
 It will install the binaries in /bin and the static libraries in /usr/lib.


docker-compose build

docker run --rm -it -v.:/export ctf-ubuntu-s6 cp /s6.zip /export

