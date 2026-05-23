# Network-public

## `update-lists.rsc`

Сгенерированный RouterOS-скрипт, обновляющий address-list'ы `ru-services` (трафик идёт напрямую, мимо VPN) и `rkn` (трафик принудительно через VPN — заблокированные РКН ресурсы). Префиксы получены из RIPE Stat по публичным ASN российских сервисов.

Стратегия импорта — простой `remove [find comment~"^#auto"]` + `add ...`: при старте импорта все автогенерируемые записи разом удаляются, затем добавляются актуальные. Ручные записи (без префикса `#auto` в комментарии) не затрагиваются.

### Raw URL

```
https://raw.githubusercontent.com/tolmachov/Network-public/main/update-lists.rsc
```

## Содержит

~3360 IPv4-префиксов, агрегированных из 426 ASN.

### `ru-services` (трафик напрямую)

- **Операторы связи:** Ростелеком, МТС, Билайн, МегаФон
- **Банки:** Сбер, Т-Банк, Альфа-банк, Уралсиб, Совкомбанк
- **Интернет-сервисы:** Яндекс, VK / Mail.ru, Rambler
- **Маркетплейсы:** Ozon, Avito, Wildberries, AliExpress
- **HR:** HeadHunter
- **Транспорт:** Аэрофлот, Победа
- **RU shared-хостеры:** Selectel, Timeweb, DDoS-Guard, Beget, REG.RU и др.

### `rkn` (трафик через VPN)

- **Telegram** (5 ASN)

Все данные публичные (ASN-владельцы и анонсируемые префиксы из RIPE Stat).
