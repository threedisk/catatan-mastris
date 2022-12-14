#### How to recover SQL Server SUSPECT Mode - Recovering a SQL Server 2000 Databases
Bagaimana cara me-recover Database dari SQL Server 2000 yang masuk mode SUSPECT. ( kurang lebih begitu translate-nya CMIIW)  

Beberapa waktu yang lalu, sedang ada kendala tentang aplikasi POS yang digunakan sedang terjadi gangguan dari segi database tidak bisa diakses. Berkali-kali mencari solusi di search engine dan baru ketemu solusi yang mantep banget dan akhirnya bisa running lagi SQL Server-nya.  

Solusi tersebut ditemukan dalam web [sqlservergeeks.com](https://www.sqlservergeeks.com/sql-server-suspect-mode-recovering-a-sql-server-2000-database)

Langsung saja.

1. Masuk ke Query Analyzer
2. Ketikkan dikolom script,  
```
EXEC sp_configure 'Allow updates','1'
Reconfigure with override
```
kemudian  
```
UPDATE master.dbo.sysdatabases
SET Status = -32768
WHERE [Name] = 'nama database'
GO
```
3. Script diatas akan membuat database yang awalnya suspect menjadi offline/readonly/emergency
4. Setelah database sudah ke mode emergency, ketikkan script dibawah ini. Script tersebut digunakan untuk membuat database tersebut menjadi single user (hanya bisa dibuka oleh 1 user/ 1 koneksi)
```
EXEC sp_dboption 'nama Database','Single User','TRUE'
```
5. Langkah selanjutnya adalah me-rebuild file Transactional Log dari database
`DBCC REBUILD_LOG('nama database','lokasi log database')`
```
DBCC REBUILD_LOG('nama database','D:\database\database_log.LDF')
```
Keterangan :
* nama database adalah database yang akan di-recovery
* lokasi log database adalah tempat dimana file log hasil rebuild dari database tersebut akan disimpan.

6. Setelah itu coba ketikkan perintah
```
DBCC CHECKDB('nama database')
```
Perintah tersebut digunakan untuk mengecek database, apakah database tersebut sudah terbebas dari error atau corrupt. Lihat log apakah database tersebut ada kendala tertulis atau tidak. Jika tidak ada error/warning maka harusnya database sudah bisa diakses lagi.

7. Jika database sudah bisa diakses kembali, tinggal masuk ke Database Properties dan kemudian un-check opsi DBO User Only Restricted Access

8. Jika database masih belum bisa diakses, coba script seperti dibawah ini.
```
DBCC CHECKDB('nama database',REPAIR_ALLOW_DATA_LOSS)
```
Script tersebut biasanya agak beresiko karena akan ada data yang sengaja dihapus karena data tersebut yang bikin korup atau error database tersebut Gunakan opsi terakhir itu jika benar-benar kepepet istilahnya.


CMIIW