<!-- markdownlint-disable MD033 -->

# The mossdef.org packages documentation

This is documentation for packages for OpenWrt devices created/maintained under the Melmac Open Source Software Development Foundation (MOSSDeF). While some of these are packages are already available from official OpenWrt release/snapshots repositories/feeds, [the ipk packages repo](https://ipk.mossdef.org)/[the apk packages repo](https://apk.mossdef.org) usually contain newer versions. You can also browse/check-out the [source code](https://source.mossdef.org).


- [The mossdef.org packages documentation](#the-mossdeforg-packages-documentation)
  - [How to use](#how-to-use)
    - [On your OpenWrt device](#on-your-openwrt-device)
      - [On your OpenWrt device with opkg](#on-your-openwrt-device-with-opkg)
        - [Add OPKG/IPK repository to your OpenWrt device (GitHub)](#add-opkgipk-repository-to-your-openwrt-device-github)
        - [Add OPKG/IPK repository to your OpenWrt device (jsDelivr)](#add-opkgipk-repository-to-your-openwrt-device-jsdelivr)
      - [On your OpenWrt device with apk](#on-your-openwrt-device-with-apk)
        - [Add APK repository to your OpenWrt device (GitHub)](#add-apk-repository-to-your-openwrt-device-github)
        - [Add APK repository to your OpenWrt device (jsDelivr)](#add-apk-repository-to-your-openwrt-device-jsdelivr)
    - [Image Builder](#image-builder)
      - [Image Builder with opkg](#image-builder-with-opkg)
        - [Add OPKG/IPK repository to Image Builder (GitHub)](#add-opkgipk-repository-to-image-builder-github)
        - [Add OPKG/IPK repository to Image Builder (jsDelivr)](#add-opkgipk-repository-to-image-builder-jsdelivr)
      - [Image Builder with apk](#image-builder-with-apk)
        - [Add APK repository to Image Builder (GitHub)](#add-apk-repository-to-image-builder-github)
        - [Add APK repository to Image Builder (jsDelivr)](#add-apk-repository-to-image-builder-jsdelivr)
    - [SDK](#sdk)
  - [Description of packages](#description-of-packages)
    - [adblock-fast and luci-app-adblock-fast](#adblock-fast-and-luci-app-adblock-fast)
    - [https-dns-proxy and luci-app-https-dns-proxy](#https-dns-proxy-and-luci-app-https-dns-proxy)
    - [luci-app-advanced-reboot](#luci-app-advanced-reboot)
    - [netclient](#netclient)
    - [pbr and luci-app-pbr](#pbr-and-luci-app-pbr)
  - [Description of outdated/obsolete packages](#description-of-outdatedobsolete-packages)
    - [antminer-monitor](#antminer-monitor)
    - [fakeinternet and luci-app-fakeinternet](#fakeinternet-and-luci-app-fakeinternet)
    - [libcurl with HTTP/3 and QUIC support](#libcurl-with-http3-and-quic-support)
    - [luci-app-easyflash](#luci-app-easyflash)
    - [luci-mod-alt-reboot](#luci-mod-alt-reboot)
    - [luci-theme-material-old](#luci-theme-material-old)
    - [nebula](#nebula)
    - [simple-adblock and luci-app-simple-adblock](#simple-adblock-and-luci-app-simple-adblock)
    - [slider-support](#slider-support)
    - [vpnbypass and luci-app-vpnbypass](#vpnbypass-and-luci-app-vpnbypass)
    - [vpn-policy-routing and luci-app-vpn-policy-routing](#vpn-policy-routing-and-luci-app-vpn-policy-routing)
    - [wlanblinker and luci-app-wlanblinker](#wlanblinker-and-luci-app-wlanblinker)
    - [wireshark-helper and luci-app-wireshark-helper](#wireshark-helper-and-luci-app-wireshark-helper)
  - [About MOSSDeF](#about-mossdef)


## <a name='Howtouse'></a>How to use

### <a name='OnyourOpenWrtdevice'></a>On your OpenWrt device

#### <a name='OnyourOpenWrtdevicewithopkg'></a>On your OpenWrt device with opkg

The ipk binaries repository is currently hosted at [GitHub](https://github.com). If you have problems accessing [the MOSSDeF ipk packages repo](https://ipk.mossdef.org) or access to [GitHub](https://github.com) may be blocked at the location where your router is installed, skip to the [Add OPKG/IPK repository to your OpenWrt device (jsDelivr)](#add-opkgipk-repository-to-your-openwrt-device-jsdelivr) section. Both repositories use HTTPS protocol and require one of the SSL support packages to be installed on your router.

##### Add OPKG/IPK repository to your OpenWrt device (GitHub)

```sh
opkg update
opkg install wget-ssl
echo -e -n 'untrusted comment: OpenWrt usign key of Stan Grishin\nRWR//HUXxMwMVnx7fESOKO7x8XoW4/dRidJPjt91hAAU2L59mYvHy0Fa\n' > /etc/opkg/keys/7ffc7517c4cc0c56
sed -i '/stangri_repo/d' /etc/opkg/customfeeds.conf
echo 'src/gz stangri_repo https://ipk.mossdef.org' >> /etc/opkg/customfeeds.conf
opkg update
```

##### Add OPKG/IPK repository to your OpenWrt device (jsDelivr)

```sh
opkg update
opkg install wget-ssl
echo -e -n 'untrusted comment: OpenWrt usign key of Stan Grishin\\nRWR//HUXxMwMVnx7fESOKO7x8XoW4/dRidJPjt91hAAU2L59mYvHy0Fa\\n' > /etc/opkg/keys/7ffc7517c4cc0c56
sed -i '/stangri_repo/d' /etc/opkg/customfeeds.conf
echo 'src/gz stangri_repo https://cdn.jsdelivr.net/gh/mossdef-org/ipk.mossdef.org' >> /etc/opkg/customfeeds.conf
opkg update
```

Please note that there may be delay in [jsDelivr CDN](https://cdn.jsdelivr.net/gh/mossdef-org/ipk.mossdef.org) cache updates comparing to [the MOSSDeF packages repo at GitHub](https://ipk.mossdef.org) which may cause `opkg` to pull older files and/or complain about wrong signature.

#### <a name='OnyourOpenWrtdevicewithapk'></a>On your OpenWrt device with apk

The apk binaries repository is currently hosted at [GitHub](https://github.com). If you have problems accessing [the MOSSDeF apk packages repo](https://apk.mossdef.org) or access to [GitHub](https://github.com) may be blocked at the location where your router is installed, skip to the [Add APK repository to your OpenWrt device (jsDelivr)](#add-apk-repository-to-your-openwrt-device-jsdelivr) section. Both repositories use HTTPS protocol and require one of the SSL support packages to be installed on your router.

##### Add APK repository to your OpenWrt device (GitHub)

```sh
wget https://apk.mossdef.org/apk.mossdef.org.pem -O /etc/apk/keys/apk.mossdef.org.pem
echo 'https://apk.mossdef.org/packages.adb' > /etc/apk/repositories.d/apk.mossdef.org.list
apk update
```

##### Add APK repository to your OpenWrt device (jsDelivr)

```sh
wget https://apk.mossdef.org/apk.mossdef.org.pem -O /etc/apk/keys/apk.mossdef.org.pem
echo 'https://cdn.jsdelivr.net/gh/mossdef-org/apk.mossdef.org/packages.adb' > /etc/apk/repositories.d/apk.mossdef.org.list
apk update
```

Please note that there may be delay in [jsDelivr CDN](https://cdn.jsdelivr.net/gh/mossdef-org/apk.mossdef.org) cache updates comparing to [the MOSSDeF apk packages repo at GitHub](https://apk.mossdef.org) which may cause `apk` to pull older files and/or complain about wrong signature.

### <a name='ImageBuilder'></a>Image Builder

#### <a name='ImageBuilderwithopkg'></a>Image Builder with opkg

The ipk binaries repository is currently hosted at [GitHub](https://github.com). If you have problems accessing [the MOSSDeF ipk packages repo](https://ipk.mossdef.org) or access to [GitHub](https://github.com) may be blocked at the location where your router is installed, skip to the [Add OPKG/IPK repository to Image Builder (jsDelivr)](#add-opkgipk-repository-to-image-builder-jsdelivr) section.

##### Add OPKG/IPK repository to Image Builder (GitHub)

Add the following line:

```sh
src/gz stangri_repo https://ipk.mossdef.org
```

to the `repositories.conf` file inside your Image Builder directory. You can use the following shell script code to achieve that:

```sh
sed -i '/stangri_repo/d' repositories.conf
sed -i '4 i\src/gz stangri_repo https://ipk.mossdef.org' repositories.conf
```

##### Add OPKG/IPK repository to Image Builder (jsDelivr)

Add the following line:

```sh
src/gz stangri_repo https://cdn.jsdelivr.net/gh/mossdef-org/ipk.mossdef.org
```

to the `repositories.conf` file inside your Image Builder directory. You can use the following shell script code to achieve that:

```sh
sed -i '/stangri_repo/d' repositories.conf
sed -i '4 i\src/gz stangri_repo https://cdn.jsdelivr.net/gh/mossdef-org/ipk.mossdef.org' repositories.conf
```

#### <a name='ImageBuilderwithapk'></a>Image Builder with apk

The apk binaries repository is currently hosted at [GitHub](https://github.com). If you have problems accessing [the MOSSDeF apk packages repo](https://apk.mossdef.org) or access to [GitHub](https://github.com) may be blocked at the location where your router is installed, skip to the [Add APK repository to Image Builder (jsDelivr)](#add-apk-repository-to-image-builder-jsdelivr) section.

##### Add APK repository to Image Builder (GitHub)

Add the following line:

```sh
https://apk.mossdef.org/packages.adb
```

to the `repositories` file inside your Image Builder directory. You can use the following shell script code to achieve that:

```sh
wget https://apk.mossdef.org/apk.mossdef.org.pem -O keys/apk.mossdef.org.pem
sed -i '/apk.mossdef.org/d' repositories
echo 'https://apk.mossdef.org/packages.adb' >> repositories
```

##### Add APK repository to Image Builder (jsDelivr)

Add the following line:

```sh
https://cdn.jsdelivr.net/gh/mossdef-org/apk.mossdef.org/packages.adb
```

to the `repositories` file inside your Image Builder directory. You can use the following shell script code to achieve that:

```sh
wget https://apk.mossdef.org/apk.mossdef.org.pem -O keys/apk.mossdef.org.pem
sed -i '/apk.mossdef.org/d' repositories
echo 'https://cdn.jsdelivr.net/gh/mossdef-org/apk.mossdef.org/packages.adb' >> repositories
```

### <a name='SDK'></a>SDK

The packages source code is available in the MOSSDeF packages source on [GitHub](https://source.mossdef.org)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/source.mossdef.org/). Individual packages are also available in their own repositories at [GitHub](https://github.com/mossdef-org/). Check out the code for the individual packages you want into your SDK's `package` folder or for luci apps into the `package/luci/applications` folder.

## <a name='Descriptionofpackages'></a>Description of packages

### <a name='adblock-fastluci-app-adblock-fast'></a>adblock-fast and luci-app-adblock-fast

This service provides lightweight and very fast dnsmasq-based ad blocking. Please see the README at [GitHub](https://docs.mossdef.org/adblock-fast/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/adblock-fast/README.md) and [OpenWrt Forum Thread](https://forum.openwrt.org/t/adblock-fast-ad-blocking-service-for-dnsmasq-smartdns-and-unbound/) for further information. This package is an improved version of [simple-adblock](#simple-adblockluci-app-simple-adblock).

### <a name='https-dns-proxyluci-app-https-dns-proxy'></a>https-dns-proxy and luci-app-https-dns-proxy

This is a lean RFC8484-compatible DNS-over-HTTPS (DoH) proxy service which supports DoH servers ran by AdGuard, CleanBrowsing, Cloudflare, Google, ODVR (nic.cz) and Quad9. Please see the README at [GitHub](https://docs.mossdef.org/https-dns-proxy/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/https-dns-proxy/README.md) for further information.

### <a name='luci-app-advanced-reboot'></a>luci-app-advanced-reboot

This package enables Web UI for reboot to another partition functionality on supported (dual-partition) routers and to power off (power down) your router. Please see the README at [GitHub](https://docs.mossdef.org/luci-app-advanced-reboot/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/luci-app-advanced-reboot/README.md) and [OpenWrt Forum Thread](https://forum.openwrt.org/t/web-ui-to-reboot-to-another-partition-for-dual-partition-routers/3423) for further information.

### <a name='netclient'></a>netclient

Netclient is an automated WireGuard Management Client. Netclient is a client application for the [Netmaker](https://github.com/gravitl/netmaker) networks. [Netclient is developed by Gravitl](https://github.com/gravitl/netclient). Please see the README at [GitHub](https://docs.mossdef.org/netclient/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/netclient/README.md) and [OpenWrt Forum Thread](https://forum.openwrt.org/t/netclient-the-client-for-netmaker-networks/) for further information.

### <a name='pbrluci-app-pbr'></a>pbr and luci-app-pbr

This service can be used to enable policy-based routing for WAN/WAN6 interfaces and multiple VPN tunnels. Supported VPN protocols include: L2TP, Openconnect, OpenVPN, Softether and Wireguard. Policies can be based on domain names, IP addresses, ports or any combination of the above. This service supports policies for both outgoing and incoming traffic to target specific interfaces/tunnels. Please see the README at [GitHub](https://docs.mossdef.org/pbr/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/pbr/README.md) and [OpenWrt Forum Thread](https://forum.openwrt.org/t/policy-based-routing-pbr-package-discussion/) for further information.

## <a name='Descriptionofoutdatedobsoletepackages'></a>Description of outdated/obsolete packages

### <a name='antminer-monitor'></a>antminer-monitor

This service can be used to monitor local BITMAIN Antminers. This is just the wrapper for [Antminer Monitor python app](https://github.com/anselal/antminer-monitor). **WARNING**: Requires a router with a lot of flash, 128Mb recommended. Please see the README at [GitHub](https://docs.mossdef.org/antminer-monitor/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/antminer-monitor/README.md) for further information.

### <a name='fakeinternetluci-app-fakeinternet'></a>fakeinternet and luci-app-fakeinternet

This service can be used to fake internet connectivity for local devices.
Can be used on routers with no internet access to suppress warnings on local devices on no internet connectivity. Please see the README at [GitHub](https://docs.mossdef.org/fakeinternet/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/fakeinternet/README.md) and [OpenWrt Forum Thread](https://forum.openwrt.org/t/fakeinternet-service-package-wip/) for further information.

### <a name='libcurlwithHTTP3andQUICsupport'></a>libcurl with HTTP/3 and QUIC support

Instructions for building `libcurl` with HTTP/3 and QUIC support using out of the tree OpenSSL-QuicTLS can be found on [GitHub](https://docs.mossdef.org/curl/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/curl/README.md)

### <a name='luci-app-easyflash'></a>luci-app-easyflash

This package installs Web UI for quickly updating your router firmware if you use automated snapshots build process which produces fully customized images and uploads them to your router. Requires sysupgrade-compatible upgrade file `/tmp/firmware.img` and a one-line description (target/version/filename info) in `/tmp/firmware.tag`. WARNING: does not keep your router settings.

### <a name='luci-mod-alt-reboot'></a>luci-mod-alt-reboot

This package enables Web UI for reboot to another partition functionality on supported (dual-partition) routers and to power off (power down) your router by overwriting default System --> Reboot page. Please see the README at [GitHub](https://docs.mossdef.org/luci-mod-alt-reboot/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/luci-mod-alt-reboot/README.md) for further information. This package has been superseded by `luci-app-advanced-reboot` and is no longer developed/supported.

### <a name='luci-theme-material-old'></a>luci-theme-material-old

This package brings back the old button styles to the `luci-theme-material` on OpenWrt 18.06.0-rc2 and later. Please see the README at [GitHub](https://docs.mossdef.org/luci-theme-material-old/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/luci-theme-material-old/README.md) for further information.

### <a name='nebula'></a>nebula

Nebula is a scalable overlay networking tool with a focus on performance, simplicity and security. It lets you seamlessly connect computers anywhere in the world. [Nebula is being developed by Slack](https://github.com/slackhq/nebula). Please see the README at [GitHub](https://docs.mossdef.org/nebula/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/nebula/README.md) and [OpenWrt Forum Thread](https://forum.openwrt.org/t/slacks-nebula-on-openwrt-discussion-thread/) for further information.

### <a name='simple-adblockluci-app-simple-adblock'></a>simple-adblock and luci-app-simple-adblock

This service provides lightweight and very fast dnsmasq-based ad blocking. Please see the README at [GitHub](https://docs.mossdef.org/simple-adblock/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/simple-adblock/README.md) and [OpenWrt Forum Thread](https://forum.openwrt.org/t/simple-adblock-fast-lightweight-and-fully-uci-luci-configurable-ad-blocking/1327) for further information. This package has been obsoleted by [adblock-fast](#adblock-fastluci-app-adblock-fast).

### <a name='slider-support'></a>slider-support

This package enables switching between `Router`, `Access Point` and `Wireless Repeater` modes of operation for supported routers equipped with slider switch. It also sets the correct `current mode` setting for the `WLAN Blinker` service (README at [GitHub](https://docs.mossdef.org/wlanblinker/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/wlanblinker/README.md)). Please see the README at [GitHub](https://docs.mossdef.org/slider-support/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/slider-support/README.md) for further information.

### <a name='vpnbypassluci-app-vpnbypass'></a>vpnbypass and luci-app-vpnbypass

This service can be used to enable split tunneling for outgoing traffic for a single OpenVPN tunnel used as the default gateway. Supports accessing domains, IP ranges outside of your OpenVPN tunnel (bypassing OpenVPN tunnel) over IPv4. Please see the README at [GitHub](https://docs.mossdef.org/vpnbypass/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/vpnbypass/README.md) and [OpenWrt Forum Thread](https://forum.openwrt.org/t/vpn-bypass-split-tunneling-service-luci-ui/) for further information. This package has been obsoleted by [pbr](#pbrluci-app-pbr).

### <a name='vpn-policy-routingluci-app-vpn-policy-routing'></a>vpn-policy-routing and luci-app-vpn-policy-routing

This service can be used to enable policy-based routing for WAN/WAN6 interfaces and multiple VPN tunnels. Supported VPN protocols include: L2TP, Openconnect, OpenVPN and Wireguard. Policies can be based on domain names, IP addresses, ports or any combination of the above. This service supports policies for both outgoing and incoming traffic to target specific interfaces/tunnels. Please see the README at [GitHub](https://docs.mossdef.org/vpn-policy-routing/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/vpn-policy-routing/README.md) and [OpenWrt Forum Thread](https://forum.openwrt.org/t/vpn-policy-based-routing-web-ui-discussion/) for further information. This package has been obsoleted by [pbr](#pbrluci-app-pbr).

### <a name='wlanblinkerluci-app-wlanblinker'></a>wlanblinker and luci-app-wlanblinker

This service can be used to indicate WLAN status by blinking the unused LED. Please see the README at [GitHub](https://docs.mossdef.org/wlanblinker/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/wlanblinker/README.md) for further information.

### <a name='wireshark-helperluci-app-wireshark-helper'></a>wireshark-helper and luci-app-wireshark-helper

This service can be used to configure router to sniff packets to/from monitored device on the device running Wireshark app. Please see the README at [GitHub](https://docs.mossdef.org/wireshark-helper/)/[jsDelivr](https://cdn.jsdelivr.net/gh/mossdef-org/docs.mossdef.org/wireshark-helper/README.md) for further information.

<!-- markdownlint-disable MD033 -->

## <a name='AboutMOSSDeF'></a>About MOSSDeF

MOSSDeF, fighting global warming by creating cool software since 2004.

<script defer src='https://static.cloudflareinsights.com/beacon.min.js' data-cf-beacon='{"token": "911798f2c34b45338f8f8182830a3eb6"}'></script>
