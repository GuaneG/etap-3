# Etap 3 — İlk Mini ETL

> Yol haritamın 3. etabı. requests + BeautifulSoup + Pandas + SQLAlchemy ile kurduğum ilk gerçek ETL pipeline'ı.

Bir siteden veri kazıyıp (**Extract**), Pandas ile temizleyip (**Transform**), PostgreSQL'e yükleyip (**Load**), üstüne SQL analiz çalıştıran uçtan uca akış. Kaynak: [books.toscrape.com](https://books.toscrape.com) (scraping için yapılmış sandbox site).

## Mimari
```
books.toscrape.com ──scrape──► Pandas DataFrame ──temizle──► PostgreSQL ──SQL──► analiz
     (Extract)                    (Transform)                  (Load)
```

## Kullanılan teknolojiler
- **Python 3**
- `requests` + `beautifulsoup4` — veri kazıma (Extract)
- `pandas` — temizleme/dönüştürme (Transform)
- `sqlalchemy` + `psycopg2-binary` — veritabanına yazma (Load)
- **PostgreSQL** — hedef veritabanı

## Kaynaklar
- [Real Python — requests Library Guide](https://realpython.com/python-requests/) (GET/POST, pagination, rate limit)
- [Real Python — Beautiful Soup: Build a Web Scraper](https://realpython.com/beautiful-soup-web-scraper-python/)
- [SQLAlchemy Core Quickstart](https://docs.sqlalchemy.org/en/20/orm/quickstart.html) (`to_sql` ile DataFrame yazma)
- Güvenli pratik siteleri: [books.toscrape.com](https://books.toscrape.com) · [quotes.toscrape.com](https://quotes.toscrape.com)

## Kurulum & çalıştırma
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt

python etl.py
```
> Çalıştırmadan önce PostgreSQL bağlantı bilgilerini ayarla (<!-- TODO: env / config nasıl verilecek -->).

## Kod yapısı
Akış `extract()`, `transform()`, `load()` fonksiyonlarına bölünmüştür.

## Notlar
<!-- TODO: pagination, fiyat/puan dönüşümü, to_sql hakkında notlar -->

## ✅ Etap 3 Bitiş Kontrol Listesi
- [ ] Sayfalı bir kaynaktan tüm veriyi döngüyle çekebiliyorum
- [ ] BeautifulSoup ile CSS selector kullanarak HTML'den veri ayıklayabiliyorum
- [ ] Pandas'ta veri tipi dönüşümü ve temizleme yapabiliyorum
- [ ] DataFrame'i `to_sql` ile veritabanına yazabiliyorum
- [ ] Kodu extract/transform/load fonksiyonlarına bölebiliyorum
