pkgname=minecraft-bedrock-server-bin
pkgver=1.16.0.2
pkgrel=1
pkgdesc="Microsoft official bedrock server"
arch=('x86_64' )
url="https://minecraft.azureedge.net/bin-linux/bedrock-server-1.14.60.5.zip"
license=('APACHE')
pkgver(){
     wget -q -O - https://www.minecraft.net/en-us/download/server/bedrock/|grep bedrock-server|head -n1|sed 's/.*bedrock-server-\(.*\)\.zip.*/\1/g'
}
source=("bedrock-server-$(pkgver).zip::https://minecraft.azureedge.net/bin-linux/bedrock-server-$(pkgver).zip"
"minecraft-bedrock-server.service")
sha256sums=('d3c63666c382ef451e1432abe71f4c5a36629b2a39f71540a3c191d844c8183c'
            '2de633773f5f667d5bdc75dc37a095eb742b35f963245ee09d34b214d95747bd')


package() {
  install -Dm744 bedrock_server $pkgdir/usr/bin/bedrock_server
  install -Dm744 libCrypto.so $pkgdir/usr/lib/libCrypto.so
  install -d $pkgdir/var/share/minecraft-bedrock-server/
  cp -r behavior_packs release-notes.txt whitelist.json definitions resource_packs bedrock_server_how_to.html server.properties bedrock_server_realms.debug permissions.json structures $pkgdir/var/share/minecraft-bedrock-server/
  install -D -m644 "./minecraft-bedrock-server.service" 	"${pkgdir}/usr/lib/systemd/system/minecraft-bedrock-server.service"
}
