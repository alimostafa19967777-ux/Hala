# 🎵 YouTube Audio Telegram Bot

Этот бот позволяет скачивать **аудио с YouTube** прямо в Telegram.  
Он написан на **Python** с использованием библиотек `python-telegram-bot` (для работы с Telegram API)  
и `yt-dlp` (для скачивания аудио с YouTube).

---

## 🧩 Что делает бот
1. Получает ссылку на YouTube от пользователя.  
2. Скачивает **только аудио** с помощью `yt-dlp`.  
3. Отправляет звуковой файл обратно пользователю.  
4. Удаляет временный файл, чтобы не занимать память.  

---

## ⚙️ Установка и запуск

```bash
# 1. Клонируйте проект
git clone https://github.com/username/youtube-audio-bot.git
cd youtube-audio-bot

# 2. Установите виртуальное окружение
python -m venv venv
source venv/bin/activate  # для Linux / macOS
venv\Scripts\activate     # для Windows

# 3. Установите зависимости
pip install -r requirements.txt

# 4. Запустите бота
python bot.py
