# ⚖️ Adalet ve Hukuk: Akıllı Sözleşmelerde Fıkıh

## Özet
İslam Ticaret Hukuku (Fıkhu'l-Muamelat), yüzyıllar boyunca adil ticaretin çerçevesini çizmiştir. Bu modül, bu kuralları modern **Akıllı Sözleşmelere (Smart Contracts)** dönüştürmeyi amaçlar. Artık kadıya gitmeye gerek yok; kod hükmü verir.

## Dijital Hukuk Katmanları

### 1. `Halal-Check` Kütüphanesi
Yazılımcıların ticaret uygulamalarına entegre edebileceği açık kaynak bir denetim kütüphanesi.
*   **Faiz (Riba) Kontrolü**: İşlemde garanti edilmiş, riske dayanmayan bir getiri var mı? (Varsa -> `RejectionError: RibaDetected`).
*   **Belirsizlik (Garrar) Kontrolü**: Satılan malın niteliği veya teslim tarihi belirsiz mi?
*   **Kumar (Maysir) Kontrolü**: İşlem şansa mı dayalı?

### 2. Standart Sözleşme Şablonları
Blok zinciri üzerinde çalışan hazır şablonlar:
*   **Mudaraba Sözleşmesi**: Emek-Sermaye ortaklığı. Kar oranları baştan koda girilir. Zarar olursa sermayedardan düşülür. Dağıtım otomatiktir.
*   **Muşaraka Sözleşmesi**: Sermaye-Sermaye ortaklığı. Kar/Zarar hisse oranına göre anlık dağıtılır.
*   **Murabaha Sözleşmesi**: Peşin alıp vadeli satma (Cost-plus). Kar marjı şeffaf ve sabittir. Gecikme faizi işlemez (ceza hayır kurumuna gider).

### 3. Merkeziyetsiz Tahkim (Digital Qadi)
Bir anlaşmazlık olduğunda (örneğin yazılım teslim edilmedi):
*   Taraflar, sistemden rastgele seçilen veya önceden belirlenmiş **Hakemlere (Jüri)** başvurur.
*   Hakemler delilleri (kod commitleri, mesajlar) inceler ve oy birliğiyle karar verir.
*   Karar (örneğin paranın iadesi), Akıllı Sözleşme tarafından zorla uygulanır (Force Execution).

## Vizyon
"Kod Kanundur" (Code is Law) değil, **"Şeriat Koddur" (Sharia is Code)**.
Adaleti bürokratların insafından kurtarıp, matematiğin kesinliğine emanet ediyoruz.
