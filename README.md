PHP:7.3-FPM ( ctn name = php-service )
    - port: 9000  _(dich vu se lang nghe o cong 9000 cua ctn)
    - Cài mysqli, pdo_mysql:
        * docker-php-ext-install mysqli
        * docker-php-ext-install pdo_mysql
    - set Thu muc lam viec mac dinh khi ctn chay: /home/site/site1

APACHE HTTPD: ( ctn name = httpd-service )
    - port: 80, 443  _(dich vu se lang nghe o cong 80 va 443 cua ctn)
    - config: /usr/local/apache2/conf/httpd.conf ( file cau hinh HTTPd ben trong container. Theo document cua Image huong dan. Sua nay minh can trich xuat file nay ra thu muc may host, sau do override no de custom config)
        * Nap : mod_proxy, mod_proxy_fcgi (Muc dinh cua cac utils nay la kich hoat viec doc cac file co duoi chi dinh)
        * Thu muc lam viec mac dinh khi contaner khoi chay: /home/site/site1
        * Index mac dinh: index.php index.html _(cho phep chay mac dinh file nay khi co request den thu muc)
        * Add PHPHandeler: AddHandler "proxy:fcgi://php-service:9000"   _(Khi httpd doc file co duoi la .php, no se goi toi dich vu php-service de execute no)
    
MYSQL: (ctn name = mysql-service)
    - port: 3304  _(dich vu se lang nghe o cong 3304 cua ctn)
    - config: /etc/mysql/my.cnf
            * default-authenication-plugin=mysql_native_password
    - databases folder: /var/lib/mysql -> /home/bay/mycode/db   _(anh xa thu muc chua database trong ctn ra ben ngoai may host)
    - MYSQL_ROOT_PASSWORD: 123abc    // cac bien nay la bien moi truong, set ban dau cho container
    - MYSQL_DATABASE: dbsite
    - MYSQL_USER: siteuser
    - MYSQL_PASSWORD: sitepass

NETWORK:
    - bridge
    - my-network    

VOLUME: dir-site
    - bind, devide = /home/bay/mycode/     // share thu muc /mycode/ tren may host cho cac container=> may host cung nhu cac container deu co the update thu muc nay