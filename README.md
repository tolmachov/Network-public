# Network-public

Публичная зеркальная публикация артефактов из приватного `Network`-репо для MikroTik роутера.

## `update-lists.rsc`

Сгенерированный RouterOS-скрипт, обновляющий address-list'ы `bypass-vpn` (трафик идёт напрямую, в обход VPN) и `force-vpn` (трафик принудительно через VPN). Префиксы получены из RIPE Stat по публичным ASN российских сервисов.

Скрипт использует **atomic mark-then-sweep**: помечает существующие `#auto` записи как `#stale`, добавляет свежие, удаляет оставшиеся `#stale` — в любой момент времени каждый "нужный" префикс присутствует в листе.

Применяется на роутере раз в сутки через `/system scheduler` (фетч + `/import`).

### Raw URL

```
https://raw.githubusercontent.com/tolmachov/Network-public/main/update-lists.rsc
```

## Содержит

Список ~3300 IPv4-префиксов российских сервисов, агрегированных из ~425 ASN: операторы связи (Ростелеком, МТС, Билайн, МегаФон), банки (Сбер, Т-Банк, Альфа, Уралсиб, Совком), интернет-сервисы (Яндекс, VK, Rambler, hh.ru), маркетплейсы (Ozon, Avito, WB, AliExpress), HR (HeadHunter), Aeroflot и пул RU shared-хостеров (Selectel, Timeweb, DDoS-Guard, Beget, REG.RU и др.). Плюс пять ASN Telegram в `force-vpn`.

Все данные публичные (ASN-владельцы и анонсируемые префиксы из RIPE Stat).
