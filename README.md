[![Actions Status](https://github.com/delphinus/p5-App-efm_perl/workflows/test/badge.svg)](https://github.com/delphinus/p5-App-efm_perl/actions)
# NAME

efm-perl - perl -c executable with errorformat friendly outputs.

# SYNOPSIS

efm-perl \[options\]

    Options:
      --filename, -f [filename]    Filename to lint. This is mandatory.
      --lib, -I [paths]            Additional paths for $PERL5LIB.
      --verbose, -v                Print all outputs.
      --help, -h                   Show help message.
      --version                    Show the version string.

    # load the script from -f option
    efm-perl -f /path/to/script.pl

    # load the script from STDIN but filter out by filename from -f option
    cat /tmp/script.pl | efm-perl -f /path/to/script.pl

# OPTIONS

- **--lib**, **-I**

    Additional paths for `PERL5LIB`

- **--filename**, **-f**

    Filename to lint. This is mandatory.

- **--verbose**, **-v**

    Print out all outputs. Without this, it shows errors only.

- **--help**, **-h**

    Print a help message.

# DESCRIPTION

This is a tiny script to use with [mattn/efm-langserver](https://github.com/mattn/efm-langserver).
It parses `perl -c` outputs and arrange them to errorformat-friendly ones.

For efm-langserver, set config.yaml as below.

    tools:
      efm-perl: &efm-perl
        lint-command: efm-perl -f ${INPUT}
        lint-ignore-exit-code: true
        lint-stdin: true
        lint-formats:
          - '%f:%l:%m'

    languages:
      perl:
        - <<: *efm-perl

# USAGE

You can install `efm-perl` with `cpanm`.

    cpanm install App::efm_perl

Or you can use simply by copying the script.

    cp script/efm-perl /path/to/your/$PATH

# LICENSE

Copyright (C) delphinus.

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.

# AUTHOR

delphinus <me@delphinus.dev>
