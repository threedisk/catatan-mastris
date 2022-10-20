#### Instalasi Multipass di Linux Mint

Multipass adalah sebuah aplikasi untuk menjalankan VM Ubuntu dengan menggunakan command line. Kalau menurut hemat saya yaitu sebuah VMWare untuk Ubuntu. 

1. Perintah untuk instalasi multipass
    ```shell
    sudo snap install multipass
    ```
2. Jika snap tidak muncul bisa menggunakan perintah untuk instalasi paket snap dengan menggunakan perintah seperti dibawah ini. Perintah tersebut digunakan untuk memindahkan file `nosnap.pref` ke Document. Kenapa harus memindahkan file tersebut? Karena dari [Snapcraft](https://snapcraft.io/docs/installing-snap-on-linux-mint) ya begitu.
    ```shell
    sudo mv /etc/apt/preferences.d/nosnap.pref ~/Documents/nosnap.backup
    sudo apt update
    sudo apt install snap
    ```
    Kemudian coba logout atau restart mesin, dan test dengan script dibawah ini.
    ```shell
    snap install hello-world
    ```
    Jika hasil output dari command tersebut muncul `hello-world!` berarti instalasi snap sudah berhasil. Kemudian install lagi multipass dengan cara seperti nomor 1.