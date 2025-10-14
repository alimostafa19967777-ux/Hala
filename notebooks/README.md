# 🎵 YouTube Audio Telegram Bot

Этот бот загружает **только аудио с YouTube** и отправляет его пользователю в **Telegram**.  
Код написан на **Python** с использованием библиотек `yt_dlp` и `python-telegram-bot`.

---

## 💻 Полный код бота

```python
import os
import yt_dlp
from telegram import Update
from telegram.ext import ApplicationBuilder, CommandHandler, MessageHandler, ContextTypes, filters

# 🔹 Токен бота, полученный от @BotFather
BOT_TOKEN = "ВАШ_ТОКЕН_БОТА"

# 🔹 Временная папка для хранения аудиофайлов
TEMP_FOLDER = "temp_audio"
os.makedirs(TEMP_FOLDER, exist_ok=True)

# 🔹 Функция обработки команды /start
async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text(
        "🎵 Привет! Отправь ссылку на видео с YouTube, и я отправлю тебе аудио напрямую."
    )

# 🔹 Основная функция обработки сообщений с ссылками
async def handle_message(update: Update, context: ContextTypes.DEFAULT_TYPE):
    url = update.message.text.strip()
    msg = await update.message.reply_text("⏳ Загрузка аудио...")

    # Настройки загрузки yt_dlp
    ydl_opts = {
        'format': 'bestaudio/best',  # Выбор лучшего качества аудио
        'outtmpl': os.path.join(TEMP_FOLDER, '%(title)s.%(ext)s'),  # Путь для сохранения
        'retries': 10,  # Количество попыток при ошибках
        'continuedl': True,  # Продолжить загрузку при обрыве
        'concurrent_fragment_downloads': 4,  # Загрузка нескольких частей одновременно
        'fragment_retries': 5  # Повтор загрузки отдельных частей при ошибке
    }

    try:
        # Загрузка аудио
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=True)
            audio_file = ydl.prepare_filename(info)
            title = info.get("title", "Аудиофайл")

        # Отправка файла пользователю
        await msg.edit_text("✅ Отправка аудиофайла...")
        with open(audio_file, 'rb') as f:
            await update.message.reply_document(document=f, caption=title)

        # Удаление временного файла после отправки
        os.remove(audio_file)
        await msg.edit_text("✅ Аудио отправлено и временный файл удалён.")
    except Exception as e:
        await msg.edit_text(f"❌ Ошибка при загрузке: {e}")

# 🔹 Настройка и запуск бота
app = ApplicationBuilder().token(BOT_TOKEN).build()
app.add_handler(CommandHandler("start", start))
app.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, handle_message))

print("🚀 Бот запущен...")
app.run_polling()





