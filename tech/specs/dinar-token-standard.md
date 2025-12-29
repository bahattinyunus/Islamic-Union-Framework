# ⚙️ Teknik Özellikler: Dijital Dinar Token Standardı (Dinar-20)

## Giriş
Bu belge, Birlik Para Birimi (Dijital Dinar) için önerilen teknik spesifikasyondur. Bu token, sadece bir değer transfer aracı değil, programlanabilir paradır.

## Teknik Özellikler

| Özellik | Değer | Açıklama |
| :--- | :--- | :--- |
| **Token Adı** | Islamic United Dinar | Resmi Para Birimi |
| **Sembol** | `IUD` (veya `DINAR`) | Borsa Kodu |
| **Ondalık** | 18 | Mikro ödemeler için yüksek hassasiyet |
| **Dayanak Varlık** | 1 Gram Saf Altın (.999) | Her token fiziksel karşılığa sahiptir |
| **Blok Zinciri** | Hilal-Chain (Cosmos SDK tabanlı) | Egemen, hızlı ve ölçeklenebilir |
| **Konsensüs** | Proof of Authority (PoA) | Üye Devletlerin Merkez Bankaları doğrulayıcıdır |

## Akıllı Sözleşme Fonksiyonları

### 1. `mintWithProof()` (Kanıtlı Para Basma)
Merkez Bankası kafasına göre para basamaz.
```solidity
function mintWithProof(uint256 amount, string memory vaultReceiptID) public onlyCentralBank {
    // 1. Altın kasası denetçisinden gelen dijital imzayı doğrula
    require(AuditOracle.verify(vaultReceiptID, amount), "Kasada karsilik altin yok!");
    
    // 2. Parayı bas
    _mint(msg.sender, amount);
}
```

### 2. `transferWithZakat()` (Zekatlı Transfer)
Kullanıcı opsiyonel olarak "Otomatik Zekat" modunu açabilir.
```solidity
function transferWithZakat(address recipient, uint256 amount) public {
    if (userSettings[msg.sender].autoZakatEnabled) {
        // Eğer üzerinden 1 yıl geçtiyse ve nisap üzerindeyse
        uint256 zakatAmount = calculateZakat(msg.sender);
        if (zakatAmount > 0) {
            _transfer(msg.sender, ZAKAT_POOL_ADDRESS, zakatAmount);
        }
    }
    _transfer(msg.sender, recipient, amount);
}
```

### 3. `applyDemurrage()` (Eksi Faiz / Stokçuluk Vergisi) - *Tartışmalı/Opsiyonel*
Ekonomiyi canlı tutmak ve para stoklamayı (kenz) önlemek için, hareketsiz cüzdanlardan çok küçük oranda kesinti yapılıp kamuya aktarılması.

## Güvenlik Modeli
*   **Çoklu İmza (Multi-Sig)**: Kritik hazine işlemleri, en az 5 üye ülkenin dijital imzasını gerektirir. Tek bir diktatör hazineyi boşaltamaz.
*   **Kuantum Koruması**: İmzalar BLS veya kafes tabanlı (Lattice) kriptografi ile korunur.
