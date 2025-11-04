# Python ile Stockfish Satranç GUI

Bu proje, Python'un `tkinter` kütüphanesi ile oluşturulmuş basit bir satranç arayüzüdür. `python-chess` kütüphanesi ile satranç mantığını yönetir ve dünyanın en güçlü satranç motorlarından biri olan `Stockfish`'i entegre ederek yapay zekaya karşı oynamanıza olanak tanır.

## 🌟 Özellikler

  * **Grafik Arayüz (GUI):** `tkinter` ile oluşturulmuş tıklanabilir ve sürükle-bırak özellikli satranç tahtası.
  * **Stockfish Entegrasyonu:** İstenilen ELO seviyesinde (kodda `elo=1218` olarak ayarlanmıştır) bir yapay zekaya karşı oynayın.
  * **Hamle Önerisi:** "Hamle Öner ve Oyna" butonu ile Stockfish'in sizin yerinize o anki en iyi hamleyi oynamasını sağlayın.
  * **Oyun Kontrolleri:**
      * **Oyunu Sıfırla:** Tahtayı başlangıç durumuna getirir.
      * **Tahtayı Çevir:** Tahtanın perspektifini (Beyaz/Siyah) değiştirir.
      * **Geri Al:** Yapılan son hamleyi geri alır.
  * **Görsel Geribildirim:** Yapılan hamleler kısa bir süreliğine tahta üzerinde vurgulanır.

## 🧩 Gereksinimler

Projenin çalışması için aşağıdaki Python kütüphanelerine ihtiyaç vardır. [cite\_start]Bu gereksinimler `requirements.txt` dosyasında listelenmiştir[cite: 1]:

  * [cite\_start]`chess`[cite: 1]: Satranç kuralları, hamleler ve tahta yönetimi için.
  * [cite\_start]`stockfish`[cite: 1]: Stockfish motoru ile Python arasında bir arayüz sağlar.
  * [cite\_start]`jupyter`[cite: 1]: Kod bir Jupyter Notebook (`.ipynb`) dosyasında sağlanmıştır.
  * `tkinter`: GUI için kullanılır (Genellikle Python standart kütüphanesiyle birlikte gelir).

Bu kütüphaneleri yüklemek için:

```bash
pip install -r requirements.txt
```

veya manuel olarak:

```bash
pip install chess stockfish jupyter
```

## ⚠️ Zorunlu Kurulum Adımı: Stockfish Motoru

Bu projenin çalışması için `stockfish` Python kütüphanesi **yeterli değildir.** Python kütüphanesi, asıl Stockfish **çalıştırılabilir motor dosyasına (.exe)** ihtiyaç duyar.

`ches-gui.ipynb` dosyasındaki kod, bu motor dosyasının yolunu manuel olarak belirtmenizi beklemektedir.

### 1\. Stockfish Motorunu İndirin

1.  Resmi indirme sayfasına gidin: [https://stockfishchess.org/download/](https://stockfishchess.org/download/)
2.  İşletim sisteminize uygun sürümü (örneğin, "Stockfish 16.1 Windows x86-64") indirin.
3.  İndirdiğiniz `.zip` dosyasını açın.

### 2\. Yolu Koda Ekleyin

Proje kodunuzun bulunduğu ana klasörde `stockfish` adında bir alt klasör oluşturun ve indirdiğiniz motor dosyalarını (özellikle `.exe` uzantılı olanı) bu klasörün içine kopyalayın.

Daha sonra `ches-gui.ipynb` dosyasını açın ve aşağıdaki satırı bulun:

```python
# Stockfish ayarları
self.stockfish = Stockfish(path=r"Kodun bulunduğu klasörü buraya girin. Klasörün içinde https://stockfishchess.org/download sitesinden indirdiğiniz alt klasör olmalı. \\stockfish\\stockfish-windows-x86-64.exe")
```

Bu satırdaki **placeholder (yer tutucu) yolu**, indirdiğiniz `.exe` dosyasının **tam yolu** ile değiştirmeniz gerekmektedir.

> **Örnek (Windows):**
> Eğer `.ipynb` dosyanız `C:\Projelerim\Chess` klasöründeyse ve motoru `C:\Projelerim\Chess\stockfish_motoru\stockfish-windows-x86-64.exe` içine kopyaladıysanız, satırı şu şekilde değiştirmelisiniz:
>
> ```python
> self.stockfish = Stockfish(path=r"C:\Projelerim\Chess\stockfish_motoru\stockfish-windows-x86-64.exe")
> ```
>
> Veya göreceli (relative) bir yol kullanarak (eğer `.exe` dosyası, notebook dosyanızla aynı dizindeki `stockfish` klasörünün içindeyse):
>
> ```python
> self.stockfish = Stockfish(path=r".\stockfish\stockfish-windows-x86-64.exe")
> ```

> **Not:** Kodda görülecek `AttributeError: 'Stockfish' object has no attribute '_stockfish'` hatası, büyük olasılıkla Stockfish motorunun yolu yanlış veya eksik girildiği için `Stockfish` nesnesinin düzgün başlatılamamasından kaynaklanmaktadır. Yukarıdaki adımı doğru yaptığınızda bu hata çözülecektir.

## 🚀 Çalıştırma

1.  Gerekli kütüphaneleri ve Stockfish motorunu kurduğunuzdan emin olun.
2.  `ches-gui.ipynb` dosyasındaki `path` değişkenini güncellediğinizden emin olun.
3.  Terminal veya komut istemcisinde proje klasörüne gidin ve Jupyter Notebook'u başlatın:
    ```bash
    jupyter notebook
    ```
4.  Tarayıcınızda açılan Jupyter arayüzünden `ches-gui.ipynb` dosyasını açın.
5.  Kodu çalıştırın. `tkinter` arayüzü yeni bir pencerede açılacaktır.