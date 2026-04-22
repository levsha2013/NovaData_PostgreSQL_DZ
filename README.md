# NovaData_PostgreSQL_DZ
Реп для ДЗ по постгрес и триггерам

# Нужно:
- Логировать все изменения пользователей (name, email, role),
- Хранить аудит изменений в отдельной таблице,
- Раз в день экспортировать только свежие изменения в CSV,
- Автоматизировать экспорт с помощью pg_cron

## таблица users
- id (serial)
- name (text)
- role (text)
- updated_at (timestamp)

## таблица users_audit
- id (serial)
- user_id (int)
- changed_at (timestamp)
- changed_by (text)
- field_changed (text)
- old_value (text)
- new_value (text)

# тех задание
1. Создайте функцию логирования изменений по трем полям.
2. Создайте trigger на таблицу users.
3. Установите расширение pg_cron.
4. Создайте функцию, которая будет доставать только свежие данные (за вчерашний день) и будет сохранять их в образе Docker по пути /tmp/users_audit_export_, а далее указываете ту дату, за который этот csv был создан.
5. Установите планировщик pg_cron на 3:00 ночи.
