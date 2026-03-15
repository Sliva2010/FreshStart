# Fresh Start — Приложение для отказа от вредных привычек

Приложение помогает пользователю отказаться от любой вредной привычки (курение, алкоголь, сладкое, соцсети и т.д.). Оно ведёт статистику, мотивирует, напоминает, награждает.

## 📱 Возможности

- **Трекер привычек** — отслеживание дней без вредной привычки
- **Таймер** — точное время (дни, часы, минуты, секунды)
- **Статистика** — графики прогресса, диаграммы успехов/срывов
- **Достижения** — система наград за milestones (3, 7, 30, 100 дней)
- **Календарь** — визуальное отображение успешных дней
- **Мотивация** — ежедневные цитаты и советы
- **Заметки** — запись мыслей и наблюдений
- **Настроение** — трекирование эмоционального состояния
- **Мини-игра** — кликер для отвлечения от желания сорваться
- **Партнёр** — демо-режим друга для поддержки
- **Визуализация** — растение растёт с каждым днём
- **Уведомления** — ежедневные напоминания через WorkManager
- **Экспорт/Импорт** — резервное копирование в JSON
- **Тёмная тема** — Material Design с динамическими цветами

## 🏗️ Архитектура

- **Язык**: Kotlin
- **Архитектура**: MVVM
- **База данных**: Room
- **Фоновые задачи**: WorkManager
- **Анимации**: Lottie, ViewPropertyAnimator, ObjectAnimator
- **Графики**: MPAndroidChart
- **Минимальный API**: 24 (Android 7.0)
- **Целевой API**: 34 (Android 14)

## 📁 Структура проекта

```
FreshStart/
├── app/
│   ├── src/main/
│   │   ├── java/com/afgsud/freshstart/
│   │   │   ├── data/
│   │   │   │   ├── model/          # Entity и data-классы
│   │   │   │   ├── local/
│   │   │   │   │   ├── dao/        # DAO интерфейсы
│   │   │   │   │   └── database/   # Room Database
│   │   │   │   └── repository/     # Repository слой
│   │   │   ├── ui/                 # Activities
│   │   │   │   ├── onboarding/
│   │   │   │   ├── auth/
│   │   │   │   ├── dashboard/
│   │   │   │   ├── statistics/
│   │   │   │   ├── achievements/
│   │   │   │   ├── motivation/
│   │   │   │   ├── settings/
│   │   │   │   ├── notes/
│   │   │   │   ├── minigame/
│   │   │   │   └── partner/
│   │   │   ├── adapter/            # RecyclerView адаптеры
│   │   │   ├── work/               # WorkManager workers
│   │   │   └── utils/              # Утилиты
│   │   ├── res/
│   │   │   ├── layout/             # XML разметки
│   │   │   ├── drawable/           # Векторные иконки
│   │   │   ├── anim/               # Анимации
│   │   │   ├── values/             # Colors, strings, themes
│   │   │   └── values-night/       # Тёмная тема
│   │   └── AndroidManifest.xml
│   └── build.gradle.kts
├── .github/workflows/
│   └── build.yml                   # GitHub Actions
├── gradle/wrapper/
│   └── gradle-wrapper.properties
├── build.gradle.kts
├── settings.gradle.kts
└── README.md
```

## 🚀 Быстрый старт

### Требования

- Android Studio Hedgehog (2023.1.1) или новее
- JDK 17
- Android SDK 34

### Сборка в Android Studio

1. Откройте проект в Android Studio
2. Дождитесь синхронизации Gradle
3. Подключите устройство или запустите эмулятор (API 24+)
4. Нажмите **Run** (Shift+F10)

### Сборка через командную строку

```bash
# Перейдите в папку проекта
cd FreshStart

# Сборка debug APK
./gradlew assembleDebug

# APK будет в: app/build/outputs/apk/debug/app-debug.apk
```

### Сборка release APK

```bash
./gradlew assembleRelease
```

## 🔧 Настройка Gradle Wrapper

Если файл `gradle-wrapper.jar` отсутствует:

### Вариант 1: Скачать через Android Studio
1. Откройте проект в Android Studio
2. IDE автоматически скачает wrapper

### Вариант 2: Скачать вручную
```bash
# Перейдите в папку проекта
cd FreshStart

# Скачайте gradle-wrapper.jar
curl -L https://raw.githubusercontent.com/gradle/gradle/master/gradle/wrapper/gradle-wrapper.jar \
  -o gradle/wrapper/gradle-wrapper.jar
```

### Вариант 3: Использовать установленный Gradle
```bash
gradle wrapper --gradle-version 8.2
```

## 📦 GitHub Actions

Проект включает workflow для автоматической сборки:

1. Запушьте код в репозиторий GitHub
2. Перейдите на вкладку **Actions**
3. Выберите workflow **Android Build**
4. Скачайте артефакт с APK

## 🎨 Кастомизация

### Изменение цветов

Откройте `res/values/colors.xml` и измените:

```xml
<color name="primary">#4CAF50</color>
<color name="primary_variant">#388E3C</color>
<color name="accent_green">#4CAF50</color>
```

### Изменение названия приложения

Откройте `res/values/strings.xml`:

```xml
<string name="app_name">Ваше название</string>
```

### Добавление цитат

В `MotivationActivity.kt` добавьте в `createDefaultQuotes()`:

```kotlin
com.afgsud.freshstart.data.model.Quote(
    text = "Ваша цитата",
    author = "Автор"
)
```

## 📝 Зависимости

Основные библиотеки:

| Библиотека | Версия | Назначение |
|------------|--------|------------|
| Kotlin | 1.9.22 | Язык |
| Room | 2.6.1 | База данных |
| WorkManager | 2.9.0 | Фоновые задачи |
| Lottie | 6.3.0 | Анимации |
| MPAndroidChart | v3.1.0 | Графики |
| Material | 1.11.0 | UI компоненты |
| Navigation | 2.7.6 | Навигация |
| DataStore | 1.0.0 | Настройки |
| Gson | 2.10.1 | JSON |

## 🔔 Уведомления

Приложение использует два канала уведомлений:

1. **Daily Reminder** — ежедневное напоминание в заданное время
2. **Achievement** — поздравления с достижениями
3. **Motivation** — мотивационные цитаты

Для Android 13+ требуется разрешение `POST_NOTIFICATIONS`.

## 📊 База данных

Таблицы Room:

| Таблица | Описание |
|---------|----------|
| users | Данные пользователя |
| day_records | Записи о днях (успех/срыв) |
| achievements | Достижения |
| notes | Заметки |
| quotes | Цитаты |
| tips | Советы |
| growth_plants | Визуализация прогресса |

## 🧪 Тестирование

```bash
# Запуск unit-тестов
./gradlew test

# Запуск instrumented-тестов
./gradlew connectedAndroidTest
```

## 📄 Лицензия

MIT License — свободное использование с указанием авторства.

## 👨‍💻 Автор

Проект создан как демонстрация современного Android-разработки с использованием Kotlin, MVVM, Room, WorkManager и Material Design 3.

## 🤝 Вклад

Проект открыт для улучшений. Основные направления:

- Добавление виджетов на главный экран
- Интеграция с Google Fit / Health Connect
- Синхронизация между устройствами
- Больше мини-игр для отвлечения
- Кастомные Lottie-анимации

## 📱 Скриншоты

Приложение включает следующие экраны:

1. **Onboarding** — 3 экрана с описанием возможностей
2. **Auth** — Регистрация (локальная)
3. **Dashboard** — Главная с таймером и статистикой
4. **Statistics** — Графики и диаграммы
5. **Achievements** — Список достижений
6. **Motivation** — Цитаты и советы
7. **Settings** — Настройки приложения
8. **Notes** — Заметки
9. **Mini Game** — Кликер для отвлечения
10. **Partner** — Демо партнёра

## ⚠️ Примечания

- Приложение хранит данные локально на устройстве
- Для работы уведомлений приложение должно быть запущено хотя бы раз
- Резервное копирование через экспорт/импорт JSON
- Минимальная версия Android: 7.0 (API 24)
