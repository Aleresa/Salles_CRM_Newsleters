# Salles CRM Newsleters

Независимая копия Telegram Mini App [CR_Newsletters](https://github.com/Aleresa/CR_Newsletters) для бота [@Salles_CRM_Newsleters_Bot](https://t.me/Salles_CRM_Newsleters_Bot/myapp).

## Возможности

- Вкладка **Поступление**: опубликованные товары в наличии, фотографии, артикулы, поиск, цены, группировка и остатки.
- **Мои заказы**: оформление с выбором менеджера, изменение и отмена, защита от повторного списания.
- **Управление**: загрузка XLS/XLSX с фотографиями, создание поступлений, ручная группировка, менеджеры, статусы, экспорт всех заказов.
- Обновление остатков по артикулу из общего Excel без изменения остальных данных о товаре.
- Уведомления о заказах в отдельный Telegram-канал с повторными попытками при сбоях.
- Авторизация через проверенный Telegram initData; администраторы определяются числовыми Telegram ID.

## Независимость от CR_Newsletters

Cloudflare Worker: `salles-crm-newsleters`. Durable Object: `NewsletterStore` внутри нового Worker, собственное имя экземпляра `salles-crm-newsleters-v1`.
Отдельные `BOT_TOKEN`, `ADMIN_IDS`, `ORDER_CHAT_ID`, `WEBHOOK_SECRET`. Реальные товары и заказы **не копируются** из прежней базы.

## Запуск

Следуйте [docs/SETUP.md](docs/SETUP.md). На Cloudflare нужно отдельно развернуть новый Worker, установить Secrets и направить `myapp` на HTTPS-адрес Worker. Приложение без `BOT_TOKEN` показывает только демо-предпросмотр, без `ORDER_CHAT_ID` создание настоящего заказа недоступно.

```sh
npm test
npm run preview
npm run deploy
```
