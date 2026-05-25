# Диаграмма деятельности: Оформление заказа в интернет-магазине

## Диаграмма деятельности

```mermaid
graph TD
    Start([Начало]) --> SelectItems(Выбрать товары)
    SelectItems --> FillAddress(Заполнить адрес доставки)
    FillAddress --> ChoosePayment(Выбрать способ оплаты)
    ChoosePayment --> ValidateData{Данные корректны?}
    
    ValidateData -- Нет --> ShowError(Показать ошибку)
    ShowError --> FillAddress
    
    ValidateData -- Да --> CreateOrder(Создать заказ)
    
    CreateOrder --> Fork{Параллельные действия}
    
    Fork --> ReserveGoods(Зарезервировать товары)
    Fork --> SendNotif(Отправить уведомление)
    
    ReserveGoods --> Join
    SendNotif --> Join
    
    Join --> ConfirmPayment(Подтвердить оплату)
    ConfirmPayment --> SaveOrder(Сохранить заказ в БД)
    SaveOrder --> End([Конец])