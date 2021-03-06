# vuci([中文](https://github.com/zhaojh329/vuci/blob/master/README_ZH.md))

![](https://img.shields.io/badge/license-GPLV3-brightgreen.svg?style=plastic "License")

VUCI - Web user interface based on [vuejs2](https://github.com/vuejs/vue) and [iView](https://github.com/iview/iview) for OpenWrt.

A new web interface with a different architecture. It doesn't use Lua anymore, but use MVVM framework. It means building HTML
pages is done on client (browser) side offloading OpenWrt device. To access any kind of system data through
[ubus](https://wiki.openwrt.org/doc/techref/ubus)(with the help of [uhttpd-mod-ubus](https://wiki.openwrt.org/doc/techref/ubus#access_to_ubus_over_http) to provide HTTP based API).

`Keep Watching for More Actions on This Space`

# [Comparison between vuejs and other frameworks](https://vuejs.org/v2/guide/comparison.html)

# How to use
Add new feed into "feeds.conf.default":
    
    src-git vuci https://github.com/zhaojh329/vuci.git

Install vuci packages:
    
    ./scripts/feeds update
    ./scripts/feeds install -a -p vuci

Select package vuci in menuconfig and compile new image.

    VUCI  --->
        <*> vuci-ui-base.......................................... VUCI Web Interface</*>


# How to develop and debug
First, enter your build directory of the vuci-ui-base

	$ cd build_dir/target-mipsel_24kc_musl/vuci-ui-base/

Then modify the configuration file according to your own environment.
You may need to modify proxyTable and host.

	vi config/index.js

Then execute the following command to start the debug server

	npm run dev

# Contributing
If you would like to help making [vuci](https://github.com/zhaojh329/vuci) better,
see the [CONTRIBUTING.md](https://github.com/zhaojh329/vuci/blob/master/CONTRIBUTING.md) file.
