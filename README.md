# Network-public

Публичная зеркальная публикация артефактов из приватного `Network`-репо для MikroTik роутера.

## `update-lists.rsc`

Сгенерированный RouterOS-скрипт, обновляющий address-list'ы `bypass-vpn` (трафик идёт напрямую, в обход VPN) и `force-vpn` (трафик принудительно через VPN). Префиксы получены из RIPE Stat по публичным ASN российских сервисов.

Стратегия импорта — простой `remove [find comment~"^#auto"]` + `add ...`: при старте импорта все автогенерируемые записи разом удаляются, затем добавляются актуальные. Ручные записи (без префикса `#auto` в комментарии) не затрагиваются.

### Raw URL

```
https://raw.githubusercontent.com/tolmachov/Network-public/main/update-lists.rsc
```

## Содержит

Список ~3300 IPv4-префиксов российских сервисов, агрегированных из ~425 ASN: операторы связи (Ростелеком, МТС, Билайн, МегаФон), банки (Сбер, Т-Банк, Альфа, Уралсиб, Совком), интернет-сервисы (Яндекс, VK, Rambler, hh.ru), маркетплейсы (Ozon, Avito, WB, AliExpress), HR (HeadHunter), Aeroflot и пул RU shared-хостеров (Selectel, Timeweb, DDoS-Guard, Beget, REG.RU и др.). Плюс пять ASN Telegram в `force-vpn`.

Все данные публичные (ASN-владельцы и анонсируемые префиксы из RIPE Stat).
