# Data Ingestion x Airflow Data Pipeline
---

## Install dengan Docker

Install docker versi terbaru, agak dapat langsung menggunakan tools compose.
- Linux atau MacOS
- Windows

## Setup Project

Pastikan sudah memiliki akun github. selanjutnya pull project dari repositori dengan script di bawah ini.
```bash
git pull git@github.com:sugengdcahyo/ingestion.git
cd ingestion
```

## Install project versi Docker

Pertama kita harus membuat beberapa folder untuk penyimpanan docker secara fisik (`docker volume`)

```bash
mkdir -p dags logs plugins
```

sehingga akan muncul directory project seperti dibawah ini

```bash
├── README.md
├── dags
├── docker-compose.yml
├── logs
└── plugins
```

Instalasi <b>pertama kali</b> menjalankan project ini.

```bash
docker compose up airflow-init
```

Install project dengan `docker compose` menggunakan perintah di bawah ini.

```bash
docker compose up -d --build
```
tunggu beberapa saat hingga proses selesai. untuk mengetahui service sudah ready, dapat kita pantau dengan perintah

```bash
docker compose logs
```
jika pada logs sudah tidak ada proses setup, maka layanan airflow dapat diakses secara default pada host `http://localhost:8080`.

selain airflow, project ini dilengkapi `celery` untuk manajemen task. layanan celery dapat diakses pada host `http://localhost:5555`.

## Membuat Direct Acyclic Graph (DAGs)
