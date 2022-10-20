#### Menginstall Python 3.8 di Ubuntu 18.04 LTS
Cara menginstall python 3.8 di Ubuntu 18.04 LTS, sebelumnya saya kira di Ubuntu 18.04 LTS tidak akan bisa diinstall Python dengan versi diatas 3.6.x. Tapi setelah googling ternyata ada cara buat install Python 3.8 di Ubuntu 18.04 LTS

1. Pastikan login root atau sudo user dan eksekusi perintah dibawah 
```
sudo apt update
sudo apt install software-properties-common
```
2. Menambahkan deadsnake PPA ke source list 
```
sudo add-apt-repository ppa:deadsnakes/ppa
```
Jika ada pernyataan Enter untuk Continue, tekan Enter saja

3. Sesudah repositori sudah enable, install Python 3.8 dengan perintah 
```
sudo apt install python3.8
```
4. Verifikasi bahwa instalasi Python 3.8 sudah berhasil dengan perintah, jika instalasi telah sukses maka akan keluar output Python 3.8.x
```
python3.8 --version
```
Itulah cara menginstall Python 3.8 di Ubuntu 18.04 LTS

Source : [Linuxize](https://linuxize.com/post/how-to-install-python-3-8-on-ubuntu-18-04/)


#### Menginstall Pip untuk Python 3.8
Tak lengkap rupanya jika Python tanpa Pip, cara untuk menginstall pip untuk Python 3.8

1. Download menggunakan curl 
```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
```
2. Install file python yang sudah didownload menggunakan Python 3.8, dengan perintah
```
python3.8 get-pip.py
```
3. Cara mengetahui pip sudah terinstall adalah dengan menggunakan perintah 
```
pip3 --version
```

Source : [Stackoverflow](https://stackoverflow.com/questions/61717006/pip-for-python-3-8)
