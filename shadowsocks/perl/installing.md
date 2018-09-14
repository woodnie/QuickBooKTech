### Installing {#installing}

On Unix like systems,either

$ perl Build.PL

$ ./Build

$ ./Build test

$ ./Build install

or

$ perl Makefile.PL

$ make

$ make test

$ make install

You might need to change make to dmake or nmake depending on the compiler toolchain used on Windows. If You have cpan, you can also install using this command

$ cpan Net::Shadowsocks