### Installing SDK on Linux Host Computer and Flashing Jetson TX2 Board Using SDK Manager

#### 1. Downloading and Installing the Required Files

**For Ubuntu Host Computer:**
1. Download the SDK Manager installation file from [NVIDIA's official site](https://developer.nvidia.com/nvidia-sdk-manager).
2. Open a terminal and navigate to the directory where you downloaded the file.
3. Run the following command to install the SDK Manager:
   
    ```
    sudo apt install ./sdkmanager_[version]-[build#]_amd64.deb
    ```

#### 2. Starting SDK Manager

You can start SDK Manager using two methods:

1. **From the Ubuntu launcher:**
    - Launch SDK Manager from the Ubuntu launcher.

2. **From the terminal:**
    - Open a terminal and run the following command:

    ```
    sdkmanager
    
    ```

#### 3. Connecting Jetson TX2 Developer Kit and Putting It into Force Recovery Mode

1. Prepare your Jetson TX2 Developer Kit as follows:
    - Connect an external HDMI display to the carrier board's HDMI port.
    - Connect a USB keyboard and mouse to a USB hub and connect the hub to the developer kit's USB Type-A port.
    - Insert the Micro-B end of the included USB Micro-B to USB A cable into the carrier board's USB Micro-AB port. Connect the other end to your Linux host computer.
    - Connect the included AC adapter to the carrier board's power jack and plug the AC adapter into a suitable electrical outlet.
    - Power off the developer kit.

2. To put the device into Force Recovery mode:
    - Press and hold the Force Recovery button.
    - Press and hold the Power button.
    - Release the Power button, then release the Force Recovery button.

#### 4. Flashing Jetson TX2 Board Using SDK Manager

1. Start SDK Manager and log in.
2. Select your Jetson TX2 board and choose the appropriate JetPack version.
3. Follow the steps to download the required software and start the flashing process.
4. Once the flashing process is complete, your Jetson TX2 board will restart and prompt you to enter initial configuration information (such as keyboard layout, username, and password). If no display is connected, you will need to perform the initial configuration "headless" using a serial application (e.g., puTTY) on the Linux host computer.

(Screenshots of the steps have been shared in the attached PDF.)




# Installing VSCodium on TX2 Board

This guide details how to install VSCodium (the open-source version of Visual Studio Code) on a TX2 board with ARM64 architecture.

## Installing Required Dependencies

First, we need to install the required dependencies to install VSCodium.

1. **Open the Terminal:**
   Open the terminal on your TX2 board.

2. **Run the following commands to update the package list and install necessary dependencies:**

   ```
   sudo apt update
   sudo apt upgrade
   sudo apt install -y software-properties-common apt-transport-https wget

   ```

   - `sudo apt update`: Updates the package list.
   - `sudo apt install -y software-properties-common apt-transport-https wget`: Installs necessary dependencies. `software-properties-common` manages software properties, `apt-transport-https` allows apt to work over HTTPS, and `wget` is a file downloading tool.

## Downloading and Installing VSCodium

VSCodium is the open-source version of Visual Studio Code and has suitable builds for ARM64 architecture.

1. **Download VSCodium for ARM64:**

   ```
   wget https://github.com/VSCodium/vscodium/releases/download/1.70.2.22230/codium_1.70.2.22230_arm64.deb -O codium_arm64.deb

   ```

   - `wget`: File downloading tool.
   - `https://github.com/VSCodium/vscodium/releases/download/1.70.2.22230/codium_1.70.2.22230_arm64.deb`: URL for the latest ARM64 build of VSCodium.
   - `-O codium_arm64.deb`: Renames the downloaded file to `codium_arm64.deb`.

2. **Install the downloaded .deb package using dpkg:**

   ```
   sudo dpkg -i codium_arm64.deb

   ```

   - `sudo dpkg -i codium_arm64.deb`: Installs the downloaded .deb package.

3. **If there are dependency issues, fix the broken dependencies:**

   ```
   sudo apt --fix-broken install

   ```

   - `sudo apt --fix-broken install`: Fixes broken or missing dependencies and installs necessary packages.

4. **Start VSCodium:**

   After the installation is complete, you can start VSCodium from the terminal with the following command:

   ```
   codium

   ```

   - `codium`: Starts the VSCodium application.

## Common Errors and Solutions

### Error: `Package architecture (amd64) does not match system architecture (arm64)`

This error occurs when trying to install a package built for AMD64 architecture on an ARM64 system. The solution is to use the appropriate builds for ARM64 architecture. In this guide, we used the ARM64 build of VSCodium.

### Error: `Invalid File Extensions`

If files in the `/etc/apt/sources.list.d/` directory are ignored due to invalid extensions, you can either rename these files to have a `.list` extension or remove unnecessary files:

```
sudo mv /etc/apt/sources.list.d/nodesource.list.save /etc/apt/sources.list.d/nodesource.list
sudo rm /etc/apt/sources.list.d/yarn.list.save

```

- `sudo mv /etc/apt/sources.list.d/nodesource.list.save /etc/apt/sources.list.d/nodesource.list`: Renames the file extension to `.list`.
- `sudo rm /etc/apt/sources.list.d/yarn.list.save`: Removes the file with an invalid extension.






### Linux Ana Bilgisayara SDK Kurulumu ve SDK Manager Kullanarak Jetson TX2 Kartının Flaşlanması

#### 1. Gerekli Dosyaların İndirilmesi ve Kurulumu

**Ubuntu Ana Bilgisayar için:**
1. SDK Manager kurulum dosyasını [NVIDIA'nın resmi sitesinden](https://developer.nvidia.com/nvidia-sdk-manager) indirin.
2. Terminali açın ve indirdiğiniz dosyanın bulunduğu dizine gidin.
3. Aşağıdaki komutu çalıştırarak SDK Manager'ı kurun:

    ```
    sudo apt install ./sdkmanager_[version]-[build#]_amd64.deb

    ```

#### 2. SDK Manager'ı Başlatma

SDK Manager'ı başlatmak için iki yöntem kullanabilirsiniz:

1. **Ubuntu başlatıcısından:**
    - Ubuntu başlatıcısından SDK Manager'ı başlatın.

2. **Terminalden:**
    - Terminali açın ve aşağıdaki komutu çalıştırın:

    ```
    sdkmanager

    ```

#### 3. Jetson TX2 Geliştirici Kitini Bağlama ve Force Recovery Moduna Alma

1. Jetson TX2 Geliştirici Kitinizi şu şekilde hazırlayın:
    - Harici bir HDMI ekranı taşıyıcı kartın HDMI portuna bağlayın.
    - Bir USB klavye ve fareyi bir USB hub'a bağlayın ve hub'ı geliştirici kitin USB Tip-A portuna bağlayın.
    - Dahil edilen USB Mikro-B'den USB A kablosunun Mikro-B ucunu taşıyıcı kartın USB Mikro-AB portuna takın. Diğer ucunu Linux ana bilgisayarınıza bağlayın.
    - Dahil edilen AC adaptörünü taşıyıcı kartın güç jakına bağlayın ve AC adaptörünü uygun bir elektrik prizine takın.
    - Geliştirici kiti kapatın.

2. Force Recovery moduna almak için:
    - Force Recovery düğmesine basılı tutun.
    - Güç düğmesine basılı tutun.
    - Güç düğmesini bırakın, ardından Force Recovery düğmesini bırakın.

#### 4. SDK Manager Kullanarak Jetson TX2 Kartını Flaşlama

1. SDK Manager'ı başlatın ve giriş yapın.
2. Jetson TX2 kartınızı seçin ve ilgili JetPack sürümünü seçin.
3. İleri adımları takip ederek gerekli yazılımları indirin ve flaşlama işlemini başlatın.
4. Flaşlama işlemi tamamlandığında, Jetson TX2 kartınız yeniden başlatılacak ve ilk yapılandırma bilgilerini (klavye düzeni, kullanıcı adı ve şifre gibi) girmeniz istenecektir. Ekran bağlı değilse, ilk yapılandırma işlemini "headless" olarak bir seri uygulaması (ör. puTTY) kullanarak yapmanız gerekecektir.


(Yapılan adımlar da görülen ekranlar pdf olarak paylaşılmıştır.)





# TX2 Kartı Üzerinde VSCodium Kurulumu

Bu rehber, TX2 kartı üzerinde ARM64 mimarisi için VSCodium'un (Visual Studio Code'un açık kaynaklı sürümü) nasıl yükleneceğini detaylandırmaktadır.

## Gerekli Bağımlılıkları Yükleme

Öncelikle, VSCodium'u yükleyebilmek için gerekli olan bağımlılıkları kurmamız gerekiyor.

1. **Terminali Açın:**
   TX2 kartınızda terminali açın.

2. **Aşağıdaki komutları çalıştırarak paket listesini güncelleyin ve gerekli bağımlılıkları kurun:**

   ```
   sudo apt update
   sudo apt upgrade
   sudo apt install -y software-properties-common apt-transport-https wget

   ```

   - `sudo apt update`: Paket listesini günceller.
   - `sudo apt upgrade`: Paket listesini günceller.
   - `sudo apt install -y software-properties-common apt-transport-https wget`: Gerekli bağımlılıkları kurar. `software-properties-common` yazılım özelliklerini yönetir, `apt-transport-https` apt'nin HTTPS üzerinden çalışmasını sağlar ve `wget` dosya indirme aracıdır.

## VSCodium'u İndirme ve Yükleme

VSCodium, Visual Studio Code'un açık kaynaklı bir sürümüdür ve ARM64 mimarisi için uygun derlemeleri bulunmaktadır.

1. **VSCodium'u ARM64 için indirin:**

   ```
   wget https://github.com/VSCodium/vscodium/releases/download/1.70.2.22230/codium_1.70.2.22230_arm64.deb -O codium_arm64.deb

   ```

   - `wget`: Dosya indirme aracıdır.
   - `https://github.com/VSCodium/vscodium/releases/download/1.70.2.22230/codium_1.70.2.22230_arm64.deb`: VSCodium'un ARM64 için derlenmiş en son sürümünün URL'sidir.
   - `-O codium_arm64.deb`: İndirilen dosyanın adını `codium_arm64.deb` olarak değiştirir.

2. **İndirilen .deb paketini dpkg ile kurun:**

   ```
   sudo dpkg -i codium_arm64.deb

   ```

   - `sudo dpkg -i codium_arm64.deb`: İndirilen .deb paketini kurar.

3. **Eğer bağımlılık sorunları varsa, eksik bağımlılıkları düzeltin:**

   ```
   sudo apt --fix-broken install

   ```

   - `sudo apt --fix-broken install`: Eksik veya kırık bağımlılıkları düzeltir ve gerekli paketleri kurar.

4. **VSCodium'u başlatın:**

   Kurulum tamamlandıktan sonra VSCodium'u terminalden şu komutla başlatabilirsiniz:

   ```
   codium

   ```

   - `codium`: VSCodium uygulamasını başlatır.

## Karşılaşılan Hatalar ve Çözümleri

### Hata: `Paket mimarisi (amd64) sistemin mimarisi (arm64) ile uyuşmuyor`

Bu hata, AMD64 mimarisi için derlenmiş bir paketi ARM64 mimarisinde çalıştırmaya çalıştığınızda ortaya çıkar. Çözüm olarak ARM64 mimarisi için uygun derlemeleri kullanmanız gerekmektedir. Bu rehberde, ARM64 mimarisi için uygun olan VSCodium paketi kullanılmıştır.

### Hata: `Geçersiz Dosya Uzantıları`

Eğer `/etc/apt/sources.list.d/` dizinindeki dosyalar geçersiz uzantılar nedeniyle yok sayılıyorsa, bu dosyaların uzantılarını `.list` olarak değiştirin veya gereksiz dosyaları silin:

```
sudo mv /etc/apt/sources.list.d/nodesource.list.save /etc/apt/sources.list.d/nodesource.list
sudo rm /etc/apt/sources.list.d/yarn.list.save

```

- `sudo mv /etc/apt/sources.list.d/nodesource.list.save /etc/apt/sources.list.d/nodesource.list`: Dosya uzantısını `.list` olarak değiştirir.
- `sudo rm /etc/apt/sources.list.d/yarn.list.save`: Geçersiz uzantılı dosyayı siler.



