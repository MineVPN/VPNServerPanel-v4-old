# VPNServerPanel v4 — Архив

> ⚠️ **Это архивная версия v4. Не поддерживается, не получает обновлений и не рекомендуется для новых установок.**
>
> Актуальная версия — [**MineServerTest (v5)**](https://github.com/MineVPN/MineServerTest).

---

## Установка

Подключитесь по SSH к свежему Ubuntu-серверу (22.04) под root и выполните:

```bash
curl -O https://raw.githubusercontent.com/MineVPN/VPNServerPanel-v4-old/main/Easy-Server-Installer-v4.sh && bash Easy-Server-Installer-v4.sh
```

Скрипт интерактивный — спросит какие сетевые интерфейсы использовать как WAN (интернет) и LAN (локальная сеть), какой режим сети (DHCP или статический IP), и установит всё необходимое.

После установки панель доступна по адресу `http://10.10.1.1/` с устройства, подключённого к LAN-интерфейсу. Логин — пароль root.

---

## Что устанавливает скрипт

- **Apache2 + PHP** — веб-панель управления
- **OpenVPN + WireGuard** — VPN-клиенты
- **dnsmasq** — DHCP и DNS для LAN-клиентов
- **iptables-persistent** — NAT через VPN-туннель
- **Базовый Health Check** — systemd timer для автоперезапуска VPN при падении
- **Защищённый DNS** — `chattr +i /etc/resolv.conf` от перезаписи DHCP

---

## Системные требования

- Ubuntu 22.04 LTS или 24.04 LTS
- Root-доступ
- Минимум 2 сетевых интерфейса (один для WAN, другой для LAN)
- Доступ в интернет на этапе установки

---

## Возможности v4

- Один активный VPN-конфиг (либо OpenVPN, либо WireGuard)
- Загрузка `.conf` / `.ovpn` файлов через веб-интерфейс
- Настройка сети (WAN/LAN) через netplan
- Базовый автоперезапуск VPN при падении (systemd timer, проверка раз в 30 секунд)
- Инструмент Ping для диагностики
- Авторизация по root-паролю

---

## Чего нет в v4 (есть в v5)

- VPN Manager с несколькими конфигами и приоритетами
- Failover на резервный конфиг при падении основного
- Kill Switch (защита от утечек трафика мимо VPN)
- Веб-терминал (shellinabox)
- Журнал событий
- Health Check daemon с мгновенной реакцией на падения
- VOIP-оптимизации (conntrack, SIP ALG, длинный DHCP lease)
- Современный UI с журналом, дашбордом, drag-and-drop

Если нужны эти возможности — устанавливайте сразу [v5](https://github.com/MineVPN/VPN).

---

## Удаление

Скрипт установщика поддерживает удаление — запустите его повторно:

```bash
sudo bash Easy-Server-Installer-v4.sh
```

И выберите соответствующий пункт в меню.

---

## Поддержка

Этот репозиторий **не поддерживается**. Issues и pull requests не принимаются.

Все вопросы — в [актуальном репозитории v5](https://github.com/MineVPN/VPN).

---

## Лицензия

Proprietary. Copyright © 2026 MineVPN Systems. All Rights Reserved.
