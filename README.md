# confuse

Create S3 Bucket
- Create
- Name (harus unik)
- Region
- Block ceklis

Create IAM Role
- Open IAM
------------------
- Klik Policies
- Create policy
- Service = S3
  Actions = All S3 Actions
  Resources = All resources
- Review Policy
  Name = FullAccessS3
---------------------
- Klik Roles
- Klik Create Roles
- Trusted Entity = AWS Service
  Use case = EC2
- Permission Policy (Pilih policy untuk s3 yang sudah dibuat sebulumnya)
- isi Role name = FullAccessS3

-------------------------
Add IAM Role to EC2
- Buka Instance menu
- pilih instance yang akan diubah role nya
- Action - Security - Modify IAM Role
- Pilih IAM role yang sudah dibuat

-------------------------------------
Menghubungkan EC2 dengan Bucket
- buka ec2
- aws s3 ls (untuk melihat semua s3)
- aws s3 ls s3://namabucket (untuk melihat isi bucket)
- aws s3 cp test.txt s3://namabucket (perintah untuk copy ke bucket)
- aws s3 cp s3://namabucket/namafile .  (untuk mendownload file dari bucket)

**********************************
Mendapatkan Akseskey id
- buka IAM
- klik user
- klik add user
- isi user name, next
- Attach poliecies
- Cari poliecy yg sudah dibuat untuk s3, next
- create user
- ketika user sudah ter create, pilih usernya
- pilih security credentials
- Create Akses Key
- Application Runnning on AWS
- Ceklis I Understand
- Create Access Key
- Copy Access Key dan Secret Access Key, pastekan di notepad, save

***********************************
Mounting S3 Bucket
- Buka EC2
- sudo amazon-linux-extras install epel -y
- sudo yum install s3fs-fuse -y
- echo akseskeyid:secretaccesskey > .pass_key
- ls -la (cek apakah sudah ter create)
- chmod 600 namafile
- mkdir mount (buat folder yang akan dimount)
- s3fs bucketname /lokasimount -o passwd_file=namapassfile

