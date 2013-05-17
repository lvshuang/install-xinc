install-xinc
============
xinc是一个PHP开发的持续集成工具，这篇文章将讲述安装过程和配置。官方文档：http://elektrischeslicht.de/xinc/book/
1.install
  安装基本按照官方文档来：pear channel-discover pear.elektrischeslicht.de
pear channel-discover pear.phing.info
pear channel-discover components.ez.no
sudo pear install Xinc/xinc
接下来并不是执行文档所述的： sudo pear run-scripts xinc/Xinc
执行该命令会报错：Could not retrieve package "xinc/Xinc" from registry。
首先我们需要安装php5-xsl。
sudo apt-get install php5-xsl

然后执行：sudo pear install xinc/Xinc-beta
命令行输出：

WARNING: "pear/PhpDocumentor" is deprecated in favor of "phpdoc/phpdocumentor"
Did not download optional dependencies: pear/VersionControl_SVN, pear/VersionControl_Git, pear/Mail, pear/PhpDocumentor, pecl/Xdebug, pear/PEAR_PackageFileManager2, use --alldeps to download automatically
xinc/Xinc can optionally use package "pear/VersionControl_SVN" (version >= 0.5.0)
xinc/Xinc can optionally use package "pear/VersionControl_Git" (version >= 0.4.4)
xinc/Xinc can optionally use package "pear/Mail" (version >= 1.2.0)
xinc/Xinc can optionally use package "pear/PhpDocumentor" (version >= 1.4.0)
xinc/Xinc can optionally use package "pecl/Xdebug" (version >= 2.0.0)
xinc/Xinc can optionally use package "pear/PEAR_PackageFileManager2" (version >= 1.0.2)
downloading Xinc-2.2.tgz ...
Starting to download Xinc-2.2.tgz (1,175,896 bytes)
.........................................done: 1,175,896 bytes
install ok: channel://pear.elektrischeslicht.de/Xinc-2.2
xinc/Xinc has post-install scripts:
/usr/share/php/Xinc/Postinstall/Nix.php
Xinc: Use "pear run-scripts xinc/Xinc" to finish setup.
DO NOT RUN SCRIPTS FROM UNTRUSTED SOURCES

倒数第二行提示我们使用：pear run-scripts xinc/Xinc完成安装。注意别忘了命令之前加 sudo.

执行后命令行输出为：
Including external post-installation script "/usr/share/php/Xinc/Postinstall/Nix.php" - any errors are in this script
PHP Warning:  declare(encoding=...) ignored because Zend multibyte feature is turned off by settings in /usr/share/php/Xinc/Postinstall.php on line 2
Inclusion succeeded
running post-install script "Xinc_Postinstall_Nix_postinstall->init()"
init succeeded
 1. Directory to keep the Xinc config files                    : /etc/xinc
 2. Directory to keep the Xinc Projects and Status information : /var/xinc
 3. Directory to keep the Xinc log files                       : /var/log
 4. Directory to install the Xinc start/stop daemon            : /etc/init.d
 5. Directory for xinc`s temporary files                       : /tmp/xinc
 6. Do you want to install the SimpleProject example           : yes
 7. Directory to install the Xinc web-application              : /var/www/xinc
 8. IP of Xinc web-application                                 : 127.0.0.1
 9. Port of Xinc web-application                               : 8080

1-9, 'all', 'abort', or Enter to continue: 
Successfully copied /usr/share/php/data/Xinc/xinc.ini.tpl  to: /usr/share/php/data/Xinc/xinc.ini
PHP Warning:  declare(encoding=...) ignored because Zend multibyte feature is turned off by settings in /usr/share/php/Xinc/Ini.php on line 2
Successfully copied /usr/share/php/data/Xinc/etc/xinc/*  to: /etc/xinc
Successfully copied /usr/share/php/data/Xinc/examples/SimpleProject  to: /var/xinc/projects
Successfully copied /usr/share/php/data/Xinc/web/.htaccess  to: /var/www/xinc
Successfully copied /usr/share/php/data/Xinc/web/*  to: /var/www/xinc
Successfully copied /usr/share/php/data/Xinc/scripts/xinc-uninstall  to: /usr/bin/xinc-uninstall
Successfully copied /usr/share/php/data/Xinc/scripts/xinc-uninstall.php  to: /usr/bin/xinc-uninstall.php
Xinc installation complete.
- Please include /etc/xinc/www.conf in your apache virtual hosts.
- Please enable mod-rewrite.
- To add projects to Xinc, copy the project xml to /etc/xinc/conf.d
- To start xinc execute: sudo /etc/init.d/xinc start
UNINSTALL instructions:
- pear uninstall xinc/Xinc
- run: /usr/bin/xinc-uninstall to cleanup installed files
[OK] Saved ini settings
Install scripts complete

至此安装完成。可使用 sudo /etc/init.d/xinc start启动服务
