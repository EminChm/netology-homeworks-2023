# Домашнее задание к занятию "Основы Terraform. Yandex Cloud"

Цель задания

    Создать свои ресурсы в облаке Yandex Cloud с помощью Terraform.
    Освоить работу с переменными Terraform.

Чеклист готовности к домашнему заданию

    Зарегистрирован аккаунт в Yandex Cloud. Использован промокод на грант.
    Установлен инструмент Yandex Cli.
    Исходный код для выполнения задания расположен в директории 02/src.
# Задание 0

    Ознакомьтесь с документацией к security-groups в Yandex Cloud.
    Запросите preview доступ к данному функционалу в ЛК Yandex Cloud. Обычно его выдают в течении 24-х часов. https://console.cloud.yandex.ru/folders/<ваш cloud_id>/vpc/security-groups Этот функционал понадобится к следующей лекции.

# Задание 1

    Изучите проект. В файле variables.tf объявлены переменные для yandex provider.
    Переименуйте файл personal.auto.tfvars_example в personal.auto.tfvars. Заполните переменные (идентификаторы облака, токен доступа). Благодаря .gitignore этот файл не попадет в публичный репозиторий. Вы можете выбрать иной способ безопасно передать секретные данные в terraform.
    Сгенерируйте или используйте свой текущий ssh ключ. Запишите его открытую часть в переменную vms_ssh_root_key.
    Инициализируйте проект, выполните код. Исправьте возникшую ошибку. Ответьте в чем заключается ее суть?
    Ответьте, что означает preemptible = true и core_fraction в параметрах ВМ? Как это может пригодится в процессе обучения? Ответ в документации Yandex cloud.

В качестве решения приложите:

    скриншот ЛК Yandex Cloud с созданной ВМ,
    скриншот успешного подключения к консоли ВМ через ssh,
    ответы на вопросы.

![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/101.png)

![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/102.png)

# Инициализируйте проект, выполните код. Исправьте возникшую ошибку. Ответьте в чем заключается ее суть?: 

code = InvalidArgument desc = the specified number of cores is not available on platform "standard-v1"; allowed core number: 2, 4
нет возможности выбора 1 ядра.

# что означает preemptible = true и core_fraction в параметрах ВМ? Как это может пригодится в процессе обучения?:

В Yandex Cloud параметр preemptible = true в настройках виртуальной машины (ВМ) указывает, что ВМ является предварительно выделенной и может быть в любой момент прервана по решению облачного провайдера. Это означает, что если какой-то другой пользователь запрашивает доступ к тому же типу ВМ, но не может получить доступ из-за нехватки ресурсов, то облачный провайдер может прервать работу ВМ с параметром preemptible = true. При этом, все данные на диске, связанные с ВМ, будут удалены.
Параметр core_fraction указывает долю ядер ЦПУ, доступных для использования на данной ВМ. Это позволяет эффективно использовать ресурсы машины, если требуется только часть ее мощности.
Использование ВМ с параметром preemptible = true и заданием параметра core_fraction может быть полезно в процессе обучения, когда возможны прерывания работы и при этом не требуется полная мощность вычислений.


# Задание 3

    Создайте в корне проекта файл 'vms_platform.tf' . Перенесите в него все переменные ВМ.
    Скопируйте блок ресурса и создайте с его помощью вторую ВМ: "netology-develop-platform-db" , cores = 2, memory = 2, core_fraction = 20. Объявите ее переменные с префиксом vm_db_ в том же файле.
    Примените изменения.
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/Screenshot%20from%202023-03-25%2017-57-34.png)
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/Screenshot%20from%202023-03-25%2017-58-37.png)

# Задание 4

    Объявите в файле outputs.tf отдельные output, для каждой из ВМ с ее внешним IP адресом.
    Примените изменения.

В качестве решения приложите вывод значений ip-адресов команды terraform output
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/Screenshot%20from%202023-03-25%2018-04-00.png)

# Задание 5

    В файле locals.tf опишите в одном local-блоке имя каждой ВМ, используйте интерполяцию по примеру из лекции.
    Замените переменные с именами ВМ из файла variables.tf на созданные вами local переменные.
    Примените изменения.
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/104.png)
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/103.png)
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/Screenshot_from_2023-03-26_18-02-15.png)
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/Screenshot%20from%202023-03-26%2021-10-48.png)

# Задание 6

    Вместо использования 3-х переменных ".._cores",".._memory",".._core_fraction" в блоке resources {...}, объедените их в переменные типа map с именами "vm_web_resources" и "vm_db_resources".
    Так же поступите с блоком metadata {serial-port-enable, ssh-keys}, эта переменная должна быть общая для всех ваших ВМ.
    Найдите и удалите все более не используемые переменные проекта.
    Проверьте terraform plan (изменений быть не должно).
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/Screenshot%20from%202023-03-26%2021-04-01.png)
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/Screenshot%20from%202023-03-26%2021-03-33.png)
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/Screenshot%20from%202023-03-26%2021-03-15.png)
