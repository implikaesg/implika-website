# İmplika web sitesi (implika.co)

Statik site. Derleme (build) adımı yok, sunucu tarafı kod yok. Bu klasörün içeriği olduğu gibi yayına alınır.

## Dosyalar

| Dosya | Görevi | Gerekli mi? |
|---|---|---|
| `index.html` | Sitenin tamamı: 12 sayfa, TR/EN metinler, stiller, menü/dil/form kodu | **Evet** |
| `assets/logo.webp` | Header ve footer logosu | **Evet** |
| `assets/fonts/*.woff2` | Manrope ve DM Mono yazı tipleri (Türkçe karakterler dahil) | **Evet** |
| `favicon.png`, `apple-touch-icon.png` | Tarayıcı sekmesi ve telefon ana ekran ikonu | Önerilir |
| `assets/og-image.png` | LinkedIn/WhatsApp paylaşım önizleme görseli | Önerilir |
| `404.html` | Yanlış adrese gelen ziyaretçiye siteyi gösterir | Önerilir |
| `robots.txt`, `sitemap.xml` | Arama motorları için | Önerilir |
| `_headers` | Cloudflare Pages önbellek ve güvenlik başlıkları | Yalnızca Cloudflare |
| `CNAME` | GitHub Pages özel alan adı | Yalnızca GitHub Pages |
| `assets/fonts/LICENSE-*.txt` | Yazı tiplerinin açık lisansı (SIL OFL) | Silmeyin |

Site dışarıdan hiçbir dosya çağırmaz. Tek dış bağlantı footer'daki LinkedIn linkidir.

## Yayına alma — Cloudflare Pages (önerilen)

1. Cloudflare panelinde **Workers & Pages → Create → Pages → Upload assets** seçin.
2. Proje adı: `implika`. Bu klasörün **içeriğini** (index.html en üst seviyede olacak şekilde) yükleyin.
3. **Custom domains → Set up a custom domain** → `implika.co` ekleyin; `www.implika.co` için de ekleyin.
4. Alan adı Cloudflare'de yönetiliyorsa DNS kayıtları otomatik oluşur. Değilse Cloudflare'in gösterdiği CNAME kaydını alan adı sağlayıcınızda ekleyin.

## Yayına alma — GitHub Pages

1. Yeni bir repo oluşturun, bu klasörün içeriğini repo köküne yükleyin.
2. **Settings → Pages → Source: Deploy from a branch → main / (root)**.
3. `CNAME` dosyası alan adını `implika.co` olarak tanımlar. Alan adı sağlayıcınızda GitHub'ın belirttiği A kayıtlarını (apex) ve `www` için CNAME kaydını ekleyin, ardından **Enforce HTTPS** seçeneğini açın.

## Bilinmesi gerekenler

- **Sayfa adresleri:** Sayfalar `implika.co/#about`, `implika.co/#contact` şeklinde açılır. Sunucuda yönlendirme ayarı gerekmez.
- **İletişim ve demo formu:** Form verisi bir sunucuya gönderilmez; ziyaretçinin e-posta uygulamasında info@implika.co adresine hazır bir e-posta açılır, metin kopyalanabilir de. Formların doğrudan gelen kutusuna düşmesi isteniyorsa bir form servisi (Formspree, Cloudflare Worker vb.) bağlanmalıdır.
- **Dil tercihi:** Ziyaretçinin TR/EN seçimi tarayıcısında saklanır; varsayılan dil Türkçedir.
- **Logo:** `assets/logo.webp` 264×88 piksel. Retina ekranlarda daha keskin görünmesi için elinizdeki yüksek çözünürlüklü logoyu (tercihen SVG) aynı adla değiştirip `index.html` içindeki `assets/logo.webp` yolunu güncelleyebilirsiniz.
- **İçerik güncelleme:** Tüm metinler `index.html` içinde, `const L={ tr:{...}, en:{...} }` bloğundadır.
