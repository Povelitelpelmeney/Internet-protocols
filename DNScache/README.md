# Кэширующий DNS сервер. 
Сервер прослушивает 53 порт. При пер-
вом запуске кэш пустой. Сервер получает от клиента рекурсивный запрос и выполняет разре-
шение запроса. Получив ответ, сервер разбирает пакет ответа, извлекает из него ВСЮ (в том
числе из полей Authority и Additional) полезную информацию, т. е. все ресурсные записи, а не
только то, о чем спрашивал клиент. Полученная информация сохраняется в кэше сервера.
Например, это может быть два хэш-массива.
Сервер регулярно просматривает кэш и удаляет просроченные записи (использует поле TTL).
## Как работает:
Содержит список IP DNS серверов к которым нужно обращаться при отстуствии информации в кеше. Кэш проверяется и обновляется при наличии новой информации.<br />
self.server - работа сервера и операции с методами<br />
self.get_records -  предназначена для получения DNS-записей (DNSRecord) из кэша по заданному имени запроса (q_name)<br />
self.data_result - предназначена для обновления кэша DNS-записей на основе результата полученного запроса<br />
self.update_cache - загрузка записей в кэш<br />
self.fetch - парсинг и обработка cache.json<br />
self.lookup - предназначена для выполнения DNS-поиска (lookup) для указанной DNS-записи (dns_record)<br />
self.get_new_zones_ip -  предназначена для извлечения IP-адресов новых зон из ответа DNS-запроса<br />
self.recieve_resp - обработка запроса<br />

