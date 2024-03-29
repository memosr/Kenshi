<h1 align="center">Kenshi</h1>

> Kurulumu basit, ne kadar süreceği belli değil. Node devamlı güncellemeler alabiliyor. Sık sık kontrol edin.

> Ödüllü ancak iyi performansı veren 200 node ödül alabilir. Devamlı güncel kalmakta önemli.

#

<h1 align="center">Donanım</h1>

> Bir node yanına kurabilirsiniz. Ancak teknik bilginiz yoksa bu sıkıntı olabilir

> Ben Contabo üzerinde kurdum. Geç kurmama rağmen 150. sıraya girdim.

>  2 CPU 2 RAM ideal 'şimdilik'

#

<h1 align="center">Kurulum</h1>

```console
# Sunucu Güncelleme
sudo apt update -y && sudo apt upgrade -y

# Burada 20 ve 60 saniye bekliyoruz
# Komutları sırasıyla girelim:
curl -sL https://deb.nodesource.com/setup_20.x -o /tmp/nodesource_setup.sh
sudo bash /tmp/nodesource_setup.sh
sudo apt install nodejs
npm install -g npm@10.2.5
sudo npm i -g @kenshi.io/unchained
sudo npm i -g @kenshi.io/unchained@latest
```

<h1 align="center">Yapılandırma işlemleri ve başlatma</h1>

```console
# conf.yaml içine girelim
sudo nano conf.yaml

# burada sadece Memo kısmını kendi adınız yapın - gerisini ben ayarladım
log: info
name: Memo
lite: true
rpc:
  ethereum:
    - https://ethereum.publicnode.com
    - https://eth.llamarpc.com
    - wss://ethereum.publicnode.com
    - https://eth.rpc.blxrbdn.com
database:
  url: postgres://<user>:<pass>@<host>:<port>/<db>
peers:
  max: 128
  parallel: 8
jail:
  duration: 5
  strikes: 5
waves:
  count: 8
  select: 50
  group: 8
  jitter:
    min: 5
    max: 15

> CTRL X Y Enter ile çıkıyoruz.


# Screen içine girelim
screen -S kenshi

# Başlatalım
unchained start conf.yaml --generate

> CTRL A D ile screenden çıkıyoruz.

# Notlar:
> Son komuttan sonra loglar akmaya başlayacak ve sync olmaya başlayacaksınız
> Kısa sürede puanlarınız gelmeye başlaycaktır.
```

> WinSCP veya mobaxterm benzeri bir uygulama ile conf.yaml dosyasını yedekleyelim.

> Veya `cat conf.yaml` komut ile çıktıyı kaydedebilirsiniz.

> conf.yaml içinde ki secret key önemli olan.

> Public keyiniz dosya içerisinde bulunmuyorsa alttaki komut ile öğrenebilirsiniz.
 ``` unchained address conf.yaml ```

> Kendinizi [burada](https://charts.mongodb.com/charts-unchained-gpust/public/dashboards/cbb6ccf6-15b2-4187-be56-ff9d2e25a48a) contributions kısmında bulabilirsiniz.

> Güncel score'unuza bakmak için [bu](https://kenshi.io/unchained) adresini tercih edebiliriz, siteye girdikten sonra hiçbir şey yapmadan biraz beklemeniz lazım score'ların yüklenmesi için.
