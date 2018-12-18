FROM php

COPY ./phpinfo.php ./phpinfo.php

RUN docker-php-ext-install pdo_mysql

CMD ["php", "-S", "0.0.0.0:9000"]
