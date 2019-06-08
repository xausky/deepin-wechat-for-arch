# Maintainer: Ding Xiao <tinocodfcdsa10@mails.tsinghua.edu.cn>
# Maintainer: Jingbei Li <i@jingbei.li>
# Maintainer: Alia Skywol <skywol@qq.com>

pkgname=deepin-wechat
pkgver=2.6.2.31
pkgrel=4
pkgdesc="Tencent WeChat Client on Deepin Wine Updated"
arch=("x86_64")
url="http://www.deepin.com/"
license=('custom')
depends=('wine' 'lib32-libldap' 'p7zip' 'xdotool' 'xorg-xwininfo' 'deepin-wine')
makedepends=('unzip' 'tar')
optdepends=('noto-fonts-cjk: Chinese fonts that wine recognizes (you can use other fonts, but you will have to configure manually on winecfg)'
	    'gnome-shell-extension-topicons-plus-huttli-git: Show tray icon on topbar on gnome instead of wine floating window')

_mirror="https://mirrors.tuna.tsinghua.edu.cn/deepin"
source=("$_mirror/pool/non-free/d/deepin.com.wechat/deepin.com.wechat_2.6.2.31deepin0_i386.deb")
sha1sums=("8e427de964b83c642ff51f180ad161c3d754ca36")

package() {
  cd ${srcdir}
  #1) Install deepin-wine wechat!
  tar -xvf data.tar.xz -C ${pkgdir}

  #2) Fix deepin-wine language to correctly print CJK characters
  cd ${pkgdir}
  chmod -x usr/share/applications/deepin.com.wechat.desktop
  sed '30a\sed -i "s/deepin-wine/LANG=zh_CN.UTF-8 wine/" $1/drive_c/deepin/EnvInit.sh' -i opt/deepinwine/apps/Deepin-WeChat/run.sh
  sed -i "s/\/opt\/deepinwine/LANG=zh_CN.UTF-8 \/opt\/deepinwine/" /opt/deepinwine/apps/Deepin-WeChat/run.sh
}
