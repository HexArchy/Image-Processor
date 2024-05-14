# Image Processor

Image Processor - это инструмент для обработки изображений, который позволяет изменять размер, применять размытие, изменять формат и сжимать изображения.

## Установка

Для установки всех зависимостей и сборки приложения выполните следующий скрипт:

```sh
./setup_and_build.sh
```

Этот скрипт автоматически определит вашу операционную систему, установит необходимые зависимости, настроит переменные окружения и соберет приложение.

## Использование

### Запуск приложения

После успешной сборки вы можете запустить приложение с помощью следующей команды:

```sh
./image-processor [flags]
```

### Доступные флаги

- `-f, --folder string` Путь к папке, содержащей изображения (по умолчанию "img")
- `-q, --quality int` Качество кодирования изображений (0-100) (по умолчанию 100)
- `-s, --size int` Размер каждого фото не будет превышать этот размер (в MB)
- `-b, --blur uint` Радиус размытия Box blur
- `-F, --format string` Формат всех фотографий в специальный формат (png, jpg, jpeg, webp)
- `-o, --output string` Директория вывода для обработанных изображений (по умолчанию "img_out")
- `-n, --name string` Специфический суффикс после имени изображения (например, "compressed_and_blurred")
- `-h, --help` Выводит всю информацию

### Примеры использования

1. Применение размытия к изображениям в папке `img` и сохранение в папку `img_out`:

```sh
./image-processor --folder img --blur 5 --output img_out
```

2. Изменение размера изображений до 1MB, изменение формата на `webp` и сохранение в папку `img_out`:

```sh
./image-processor --folder img --size 1 --format webp --output img_out
```

3. Применение всех возможных преобразований:

```sh
./image-processor --folder img --quality 80 --size 1 --blur 5 --format png --output img_out --name processed
```

## Разработка

### Установка зависимостей

Если вам нужно только установить зависимости, используйте следующую команду:

```sh
go get -u github.com/h2non/bimg
go get -u github.com/spf13/cobra
```

### Сборка

Для сборки приложения используйте следующую команду:

```sh
go build -o image-processor app/main.go
```

## Требования

- Go 1.3+
- libvips 8.3+ (8.8+ рекомендуется)