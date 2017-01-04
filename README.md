Y2M - the YaST2 meta tool
=========================

This is a simple tool to help you to checkout all YaST modules, while
maintaining the directory structure of the former svn repo.

With this tool you can

 * checkout all or just your favorite modules
 * switch all (or favorite) modules to a specific branch
 * run git pull on all (or favorite) modules

with just one command.

Note: There is no need to use this tool.
      You can do everything manually as well.

## Installation

    cd $CHECKOUTDIR
    git clone git@github.com:yast/yast-meta meta
    cd meta
    ln -s `pwd`/y2m ~/bin/

## Usage

    y2m <command> [<modules>,..]

commands

    clone        : run git clone for <modules>
    up|pull      : run git pull for a <modules>
    co|br <name> : run git checkout to switch to branch <name> for <modules>

modules

    'ALL' : applies to all current known yast modules
    'FAV' : applies to only your favorite modules, set in ~/.y2m
    <lowercase string> : applies to the named modules

## Authentication

The tool will work even without GitHub authentication, *unless* you share
an IP with the rest of your company, in which case it will fail because of
rate limiting. To get an 83 times better rate, authenticate:

Generate a new [access token](https://github.com/settings/tokens/new)
(no scopes are needed), and set up a `.netrc` file:

```sh
touch     ~/.netrc
chmod 600 ~/.netrc
echo   >> ~/.netrc "machine api.github.com login your_username password your_token"
```

## Reserved Branch and Tag Name Prefixes

In order to maintain a certain consistency between the modules there are
some prefixes that you should *not* use for your own branches/tags.
They are reserved for openSUSE or SLE releases.

Reserved prefixed for branches and tags:

 * 'openSUSE-'
 * 'SLE-'
 * 'Code-'

See also: http://en.opensuse.org/YaST_SVN_to_GIT
