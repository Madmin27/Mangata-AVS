<h1 align="center"> Mangata AVS
  
![image](https://pbs.twimg.com/profile_banners/1314872601949462530/1686804364/1500x500)


# 01.03.2024 tarihinden Daha önceden kurulum yapanlar için güncelleme yöntemi en altta yazmaktadır. [Tıkla](#güncelleme)
# Güncellemeyi yaptıktan sonra karşınıza çıkan hatalar anlamları/çözümleri için [TIKLA](#Hatalar)


## Sistem gereksinimleri:
### Ubunutu 22.04
NODE TİPİ | CPU     | RAM      | SSD     |
| ------------- | ------------- | ------------- | -------- |
| Mangata  | 2          | 4         | 40  |
  

## Kurulum

```
sudo apt-get update -y && sudo apt-get upgrade -y
```

### Docker Kurulumu
```
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
```
```
sudo apt-get update
```
```
sudo apt-get install ca-certificates curl gnupg
```
```
sudo install -m 0755 -d /etc/apt/keyrings
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
```
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
```
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
### Docker Güncelleme ve Çalıştırma
```
sudo apt update -y && sudo apt upgrade -y
```
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
```
sudo docker run hello-world
```

### Go Kurulumu

```
cd $HOME
ver="1.21.0"
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz"
rm "go$ver.linux-amd64.tar.gz"
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile
source $HOME/.bash_profile
go version
```

## EigenLayer CLI kurulumu

```
git clone https://github.com/Layr-Labs/eigenlayer-cli.git
```
```
cd eigenlayer-cli
```
```
mkdir -p build
```
```
go build -o build/eigenlayer cmd/eigenlayer/main.go
```
```
cd
```
```
sudo cp eigenlayer-cli/build/eigenlayer /usr/local/bin/
```




> Kapalı parantez dahil, `<key-ismi>` değiştirin, <> parantezleri kaldırın.

![Ekran görüntüsü 2024-02-08 124148](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/6b7700d0-d255-4e63-8162-54a8309af9cb)

```
eigenlayer operator keys create --key-type ecdsa <key-ismi>
```

> Bu komuttan sonra şifre oluşturmanızı isteyecek, şifre karmaşık olmalı. Aynı şifreyi iki kere gireceğiz.

![Ekran görüntüsü 2024-02-08 124257](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/ea8a2804-7875-4a29-b102-e1848e3e1085)

> `ecdsa` KEY bize bir `EVM` adresi, `private key` ve dosya `path` (yolu) verecek

> Buradaki bilgiler sizde de benzer şekilde çıkacak güvenli şekilde saklayın.

![Ekran görüntüsü 2024-02-08 124603](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/bed08b0c-2706-4a95-b2ae-37dbf7184a75)

> Kapalı parantez dahil, `<key-ismi>` değiştirin, <> parantezleri kaldırın.
![Ekran görüntüsü 2024-02-08 125720](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/fe3d4dc1-d278-4801-bf68-11fb32b12236)
```
eigenlayer operator keys create --key-type bls <key-ismi>
```
> Bu komuttan sonra şifre oluşturmanızı isteyecek, şifre karmaşık olmalı. Aynı şifreyi iki kere gireceğiz.

![Ekran görüntüsü 2024-02-08 125831](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/2ad73b8c-06f4-49a8-9ca4-019aee6e43fb)

> `bls` KEY ise bir `private key` verecek. Hepsini kayıt edelim.

![Ekran görüntüsü 2024-02-08 125927](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/5a2ca0fe-0e87-4141-a25f-193acf14735b)

> Keyleri listeyerek dosya yollarını kontrol ediyoruz.

![Ekran görüntüsü 2024-02-08 130326](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/58803415-318c-4750-bcc9-63470a3374ab)

```
eigenlayer operator keys list
```
## Operatör Kaydı

```
eigenlayer operator config create
```

> Sırasıyla bunlarıda yazıyorum kolaylık için, en aşağıda görselide olcak:

> y diyoruz

![Ekran görüntüsü 2024-02-08 131009](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/c244182d-dc95-45f8-a261-479c0fc6ec94)

> operator adresi olarak, `ecdsa key` oluşturduğumuzda verdiği `evm` adresini girin.

![Ekran görüntüsü 2024-02-08 131052](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/b75faaf0-c48e-47ec-885e-6e59ccca4199)

> earning operator adres yine aynı ecdsa-evm adresi girin, yukarıdaki ile aynı.

![Ekran görüntüsü 2024-02-08 131125](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/696b50cf-d746-427f-a25e-48e7b27cb7c4)

### Public RPC alma;

> goerli eth RPC isteyecek, [BURADAN](https://app.infura.io/) siteye gidiyoruz.

![Ekran görüntüsü 2024-02-08 131453](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/d7926aad-df66-483c-bd80-102416a48eda)

İlk olarak kaydınız yok ise kayıt olun, varsa giriş yapın.

![Ekran görüntüsü 2024-02-08 131720](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/e122cc33-e5c4-4f3e-99ce-5965efca7acc)

> Resimdeki gibi bir isim girip CREATE diyoruz.

![Ekran görüntüsü 2024-02-08 131825](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/7e6eb414-9bc7-4343-9d94-39bdfe3ce767)

> Ethereıum Goerli Seçiyoruz ve Save Changes butonuna basıyoruz.

![Ekran görüntüsü 2024-02-08 131938](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/c3293b6c-7ff8-45e0-a617-2c5ebbddefaa)

> Bu şekilde bir https adresi verecek onu bir yere not edelim.

![Ekran görüntüsü 2024-02-08 132102](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/2153a821-4c02-47b6-ae8d-7c417c7a78f8)

> WebSockets bölümüne gidip oradaki adresi de bir yere not edelim. Lazım olacak.

#### Kaldığımız yerden devam edelim;

> `ecdsa key` oluşturduğumuzda bize verdiği key pathi tam şekilde giriyoruz

![Ekran görüntüsü 2024-02-08 132339](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/7b60b405-61cf-4a34-80e9-d2f1e2274458)


> goerli seçiyoruz ve bitiyor. Aşağıda tamamlanmış halinin resmini ekledim.


> Bu bize operator.yaml ve metadata.json dosyalarını oluşturacak.

### Metadata İşlemleri

```
nano metadata.json
```
> Bu komutu çalıştırıp dosyanın içine girelim.

![Ekran görüntüsü 2024-02-08 132835](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/82ecf316-d0c5-4e81-ba91-5723bbe1af59)

> Bunun içindeki bilgileri dolduralım. Dolu hali

![Ekran görüntüsü 2024-02-08 133210](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/7901b26e-0181-4618-9ad6-e0026e8c58c4)

> Bu şekilde dolduruyoruz. Sonra Bu doldurduğumuz bilgileri kopyalayıp bir yere not edelim.

### Raw Public Linki oluşturma
> Kendi Github sayfamızda Repositories sayfasına gidiyoruz sağda bulunan NEW butonuna basıyoruz.

![Ekran görüntüsü 2024-02-08 133334](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/871e6659-0bee-4b97-8069-743043525638)

> Reposity Name bölümüne magnata diye isim veriyoruz Public seçiyoruz. En altta Create Repository diyoruz.

![Ekran görüntüsü 2024-02-08 133703](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/6042f423-b202-451f-a221-b59a9df72a23)

> Sonrasında size aşağıdaki gibi bir sayfa çıkacak orada READ ME seçip repoyu oluşturun.

![Ekran görüntüsü 2024-02-08 133746](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/00b5f656-fe47-4083-8c6d-d8c1f2a54ee1)

> Sağ bölümde Add File seçeneği var ona basın. Create File var ona basın.

![Ekran görüntüsü 2024-02-08 133906](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/628481cb-9512-414c-be6a-12e03990985a)

> Create File sekmesine geldiğinizde Aşağıdaki görselde olduğu gibi işlemlerinizi yapın. Node içine yazdığımız bilgilerin aynısı burada olacak.

![Ekran görüntüsü 2024-02-08 134122](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/e4867bdc-178b-4614-8682-0e1000b8bd9a)

> Bu adımları yaptıktan sonra Commit tuşuna basıyoruz.

> Commit tuşuna bastıktan sonra dosyamız yayınlanacak o dosya repo içinden basıp ulaşıyoruz. Sağ bölümde RAW kısmı var ona basıyoruz.

![Ekran görüntüsü 2024-02-08 134215](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/fceedaa1-8be7-412f-9f42-3a6c6371dd77)

> Raw tuşuna bastıktan sonra size tarayıcı da yeni bir sayfa açacaktır. Tarayıcıdaki URL bir yere not edin.

![Ekran görüntüsü 2024-02-08 134338](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/e1c4b158-4adb-4aa1-838a-d2e8d6e94a9b)

### Yukarıdaki adımları hallettiysek devam edelim

```
nano operator.yaml
```

> metadata_url için metadata.json dosyamızın public raw linkini kullanacağız.

> el_delegation_manager_address: 0x1b7b8F6b258f95Cf9596EabB9aa18B62940Eb0a8 # burda bu yazıyor olmalı

> Adımları düzgünce eklediysek CTRL + X + Y Enter yapıp çıkıyoruz. Aşağıya görselini de ekledim.

> Node içinde aldığınız Private Key dosyasını metamask içine import ediyoruz.

> Metamask> Account basıyoruz => En altta Add Account kısmı var ona basıyoruz => Hesabı içe aktar seçeneğine basıyoruz. => Sonrasında node içinden aldığımız private key girip import işlemini tamamlıyoruz. 

> Node için kurduğumuz cüzdana 0,5 - 1 arasında GOERLİ ETH gönderelim. Yeni cüzdana ETH geçtikten sonra; (Eğer goerli ETH bulamazsanız daha düşük miktarlar da olur.)


```
eigenlayer operator register operator.yaml
```

> komutunu çalıştırıp. Hem edsa hem bls şifremizi girip Logların akmasının bitmesini bekliyoruz.

```
eigenlayer operator status operator.yaml
```

> Durum kontrolü yapıyoruz. Aşağıdaki gibi çıktı almanız gerekiyor.

![Ekran görüntüsü 2024-02-09 091954](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/94f5b712-2163-4989-a295-d1c4f36d3b44)

> **Önemli!! ilk kez kuruyorsan ve metadata değişiklik yapmadıysan bu komutu girmene gerek yok!
```
eigenlayer operator update operator.yaml
```
> Meta data üzerinde herhangi bir değişiklik yaparsanız, bu komut ile güncellemeyi unutmayın.

## Mangata VS Kurulumu

### Önemli rETH ve sETH TVL miktarınız yani platforma stake miktarınızın toplamı 0,3-0,35'den fazla olmalıdır. Birazını rETH, birazını da sETH yaparak eklersiniz.

> [BURADAN](https://app.uniswap.org/swap) Uniswap'a gidiyoruz. Goereli Ağında yeni kurduğumuz cüzdan ile bağlanıyoruz. 

> İlk rETH alacağız. `rETH=0x178e141a0e3b34152f73ff610437a7bf9b83267a` kontrat adresi ile uniswapta aratıp bir miktar alıyoruz.

> Şimdi de sETH alıyoruz. `sETH= 0x1643e812ae58766192cf7d2cf9567df2c37e9b7f` kontrat adresi ile uniswapta aratıp bir miktar alıyoruz.

> [BURADAN](https://goerli.eigenlayer.xyz/) sETH ve rETH poollarına stake ediyoruz.

> Stake adımları tamamlandıktan sonra Terminalden adımlarımıza devam edelim

```
git clone https://github.com/mangata-finance/avs-operator-setup.git
```

```
cd avs-operator-setup
```

```
chmod +x run.sh
```

```
nano .env
```

![Ekran görüntüsü 2024-02-09 094222](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/694b9ef6-152d-4eb3-9046-fb44f8e435dd)

> Ekrana böyle bir sayfa gelecek buradaki düzenlememizi yapıyoruz.

> `ETH_RPC_URL` buraya infuradan aldığımız https olan PRC adresini giriyoruz.

> `ETH_WS_URL` buraya infura WSS linki giriliyor.

> `ECDSA_KEY_FILE_HOST` buradaki dosya yolunu silip node içinden alıp kaydettiğimi ECDSA key dosya yolunu ekliyoruz.

> BLS_KEY_FILE_HOST buradaki bölüme bls dosya yolunu yazıyoruz.

> `ECDSA_KEY_PASSWORD` buraya ecdsa için verdiğimiz şifreyi giriyoruz.

> `BLS_KEY_FILE_HOST` buraya bls için verdiğimiz şifreyi giriyoruz.

> Bu adımları tamamladıktan sonra CTRL X + Y Enter yaparak çıkıyoruz.

```
./run.sh opt-in
```

```
docker compose up -d
```
> Docker contianer id bulmak için

```
docker ps
```
> aldığınız ID ile aşağıdaki komutu girip, log kayıtlarının akmasını bekliyoruz.

```
docker logs -f <container_id>
```
> Aşağıdakine benzer şekilde log kayıtlarınız akmış olacak.

![Ekran görüntüsü 2024-02-09 095454](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/4b0ac864-080f-4571-b885-0d4b652b5b36)

> [BURADAN](https://discord.gg/mangata) Mangata'nın discord kanalına gidip Verify sonrasında #AVS Operator kanalına, yukarıdaki gibi görseli atıp Node Runner rolümüzü isteyelim.

> Bu arada Dokümanın orjinali'ne [BURADAN](https://github.com/ruesandora/mangata-AVS/blob/main/README.md) ulaşabilirsiniz. Rues hazırladığı dokümanı kullandım ve yeni başlayanlar için ayrıntıları ekledim.

> Rues reposunda ödüllü olduğunu ve KYC yapılabileceğini belirtmiş. Ona göre kendi kararınızı verebilirsiniz.




# Güncelleme 

> Güncelleme adımlarına başlayalım. 

> Unutmadan Stake yaptığınız rETH ve sETH miktarlarının toplamının 1ETH yi geçmesi veya eşit olması şart.

> [TIKLA](https://goerli.eigenlayer.xyz/) Aşağıdaki gibi 1ETH yi geçmiş veya eşit olmalı
![resim](https://github.com/CoinHuntersTR/Mangata-AVS/assets/63106683/62f8e068-a665-489c-9c4f-22ed776604c7)

```
cd avs-operator-setup
```

```
docker compose down
```

> .env dosyanızı yedeklemeniz gerekmekte. isterseniz nano .env yapıp direkt kopyalayın ekrandaki her şeyi

```
git reset --hard
```
```
git pull
```

```
docker compose pull
```
```
docker compose down
```

> Az önce yazdığımız kodlar ile node dosyalarımızı güncelledik. 
> bu nedenle güncellenmiş env dosyasını düzenlememiz gerekmektedir.

```
nano .env
```

![resim](https://github.com/CoinHuntersTR/Mangata-AVS/assets/63106683/aba7ddda-1bc1-40d1-9414-85f22e82e80d)

>resmideki çift süslü parantezli yerleri yedeklediğimiz dosyadan kopyalayın başka hiçbir şeye **dokunmayın**. 

>***SÜSÜLÜ PARANTEZLERİ DE SİLİN!!!***

>Eğer sizin env dosyanız resimdeki gibi değil ise aşağıdaki kodları yazın.

```
rm -rf .env
```

```
nano .env
```

> Aşağıdaki kısmı kopyalayıp bir not defterinde açın **süslü parantezleri silip** gerekli değerleri yazın. 

> Sonra da az önce boş bir sayfa olarak açtığımız .env dosyasına yapıştırın sağ tık ile yapıştırın.

```
MAIN_SERVICE_IMAGE=mangatasolutions/avs-finalizer:80ac399c2c2f103dd8de1be62c114d5090cd11cd
MAIN_SERVICE_NAME=avs-finalizer-node

#COLORBT_SHOW_HIDDEN=1
#RUST_BACKTRACE=full

# Goerli contracts deployment
AVS_REGISTRY_COORDINATOR_ADDR=0x5620cDb94BaAaD10c20483bd8705DA711b2Bc0a3

# Finalizer Service Manager RPC
AVS_RPC_URL=https://avs-aggregator-testnet.mangata.online/
# register with AVS when the node starts
OPT_IN_AT_STARTUP=true

RUST_LOG=avs=info

###############################################################################
####### TODO: Operators please update below values for your node ##############
###############################################################################

# TODO: Operators need to update this to provide connection to ETH & network nodes
CHAIN_ID=5
ETH_RPC_URL={{RPC url https://goerli.infura.io/v3/ şeklinde olacak}}
ETH_WS_URL= {{Websocket url wss://goerli.infura.io/ws/v3/ şeklinde olacak}}
SUBSTRATE_RPC_URL=wss://collator-01-ws-rollup-testnet.mangata.online:443

# TODO: Operators need to update this to their own keys, either use files or encoded JSON
# this is where your keys are stored on local storage
ECDSA_KEY_FILE_HOST=/root/.eigenlayer/operator_keys/{{eigenlayer_cüzdan_adınız}}.ecdsa.key.json
BLS_KEY_FILE_HOST=/root/.eigenlayer/operator_keys/{{eigenlayer_cüzdan_adınız}}.bls.key.json

# this is where the node binary finds the keys in the docker container
ECDSA_KEY_FILE=/app/operator_keys/ecdsa_key.json
BLS_KEY_FILE=/app/operator_keys/bls_key.json

# it is possible to pass the encoded json key directly with these env flags
# comment above both ECDSA_KEY_FILE & BLS_KEY_FILE if used
#ECDSA_KEY_JSON=
#BLS_KEY_JSON=

# TODO: Operators need to add password to decrypt the above keys
ECDSA_KEY_PASSWORD={{Şifrenizi buraya yazın}}
BLS_KEY_PASSWORD={{Şifrenizi buraya yazın}}
```


> İşiniz bittiği zaman bu resimdeki gibi gözükmesi lazım dosyanızın.

![resim](https://github.com/CoinHuntersTR/Mangata-AVS/assets/63106683/918c7b2b-033c-4a5a-9620-6af2ebf03a68)

> env ile işiniz bitince

```
docker compose up -d
```

```
docker ps
```

> Bu kod ile container id kopyalayın

```
docker logs -f {id} 
```

>Süslü parantezli kısmı silip kopyaladığınız id yi yapıştırın.


>Ardından resimdeki gibi gözükmesi lazım. 

![resim](https://github.com/CoinHuntersTR/Mangata-AVS/assets/63106683/b2ace762-4a95-4cef-a95d-795ed015c5db)

> Ama biraz sürebilir bu logların akmaya başlması şuan ağ çok yavaş.
> Resimdeki gibi Sucesfully registered yazdıysa bırakın kendi haline çok da kafaya takmayın. 
> 30dk sonra ✅ görmez iseniz logda bi sorun olmuş olabilir. 
> Telegram grubuna gelin çözelim sorunu hem rehbere de ekleriz başka karşılaşanlar için iyi olur.

> Güncelleme Rehberini Yazan : @dwtexe 
> Esenlikler Dilerim.



# Hatalar

> 24 saat sonra tekrardan buradayım.
> Evet şimdi çok fazla karşımıza çıkan herkesin sorduğu ve sormaktan sıkılmadığı hataları açıklayalım ve çözümleri varsa çözüme kavuşturalım.


### 1

> Aşağıdaki hatalara RPC errors denir. Sizle alakalı değiller biryerlerinizi yırtmak pahasına çözüm arasanız da bulamayacaksınız bu yüzden sormayı bırakın.
> Mangata'nın çözmesi gereken bir sorun bu onlardan haber bekleyeceğiz başka yapılabilecek **hiçbir şey yok**

![resim](https://github.com/Dwtexe/Mangata-AVS/assets/63106683/8fdbac8d-4b6c-43a6-aceb-07e47b30e23f)
![resim](https://github.com/Dwtexe/Mangata-AVS/assets/63106683/6da44650-3590-49ec-8d02-fa64c8c67b6f)
![resim](https://github.com/Dwtexe/Mangata-AVS/assets/63106683/d81e1339-9f99-4356-a9c3-5bd53c46ae58)

### 2

> Gelelim ikinci en çok karşılaşılan hatalar kısmına.
> Bu hatalar sizden kaynaklı aması maması yok! .env dosyanızda hata var.
> Yok olmaz öyle şey benim .env dosyasını benden iyi mi tanıyacaksınız diyebilirsiniz. Ama sizi üzecek bir haberim var... Maalesef sizden iyi tanıyorum.
> Üst taraflarda attığım .env dosyasının boş hali ile karşılaştırın ve sadece değiştirin dediğim kısımları düzgün şekilde yaptığınızdan emin olana kadar tekrar tekrar kontrol edin.
> Bazı arkadaşlar şifrelerini unuttuğu için her kısım doğru olsa da hata alıp kendilerini parçalıyorlar. Şifrenizden emin olun lütfen.


![resim](https://github.com/Dwtexe/Mangata-AVS/assets/63106683/fc7d7b20-4894-4208-a403-d0673a7063a7)
![resim](https://github.com/Dwtexe/Mangata-AVS/assets/63106683/984c1f42-1cc8-41dd-b018-383d11d22922)



> Son olarak da lütfen çözümünü bulduğunuz ya da çözemeseniz bile neden kaynaklandığını anladığınız hatalar var ise bana ulaşın.
> Telegram/Discord : @dwtexe
