# ReadMe First !!!
Магазин на минималках. Без рюшечек, блекджека и ...  

vagrant > v2.2.0 required  
***vagrant-hostmanager*** required  
vagrant plugin install vagrant-hostmanager

Внутри:
 - WordPress
 - Woocommerce
 - Storefront Theme
 - Nginx + PHP7-FPM
 - MySQL server
 - Debian  

Картинок для образцов товаров нет (без рюшечек...) очень уж непросто они генерятся  
Темплейтов по минимуму (дамп базы + nginx host config) все остальное правим кодом в конфигах по умолчанию для пакетов дистрибутива.  
Без SSL, Ansible Vault. Минимум хардкода. Основные переменные в server-**.yml
В случае нашего изолированного окружения многое избыточно.  
http://server-01/wp-admin/ - админка  
user1/user1 лог, пасс
