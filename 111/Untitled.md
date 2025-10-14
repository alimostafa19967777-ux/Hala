```python
import os         #Работа с файлами и папками
import yt_dlp     #Скачивает аудио с YouTube
from telegram import Update   #библиотеки для создания Telegram-бота.
from telegram.ext import ApplicationBuilder, CommandHandler, MessageHandler, ContextTypes, filters  

# Arabic: هنا ضع التوكن  встаالخاص بالبوت
# Russian: сюда вляется токен, полученный от BotFather
BOT_TOKEN = "8411237003:AAG4DZiXDBWOHUcaONQVGXUVXInCu_8sSUI"
q
# Arabic: هذا المجلد سيخزن الملفات الصوتية مؤقتاً
# Russian: Эта папка будет временно хранить аудиофайлы
TEMP_FOLDER = "temp_audio"
os.makedirs(TEMP_FOLDER, exist_ok=True)    #создаёт папку, если она не существует


# Arabic: هذه الدالة للتعامل مع أمر /start
# Russian: Эта функция обрабатывает команду /start...Когда пользователь отправляет /start, бот приветствует его
async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    # Arabic: رسالة ترحيبية للمستخدم
    # Russian: Используется await, так как функция асинхронная
    await update.message.reply_text(
        "🎵 Привет! Отправь ссылку на видео с YouTube, и я отправлю тебе аудио напрямую."
    )


# Arabic: هذه الدالة تتعامل مع أي رسالة تحتوي على رابط يوتيوب
# Russian: Эта функция обрабатывает любое сообщение с ссылкой на YouTube
async def handle_message(update: Update, context: ContextTypes.DEFAULT_TYPE):
    url = update.message.text.strip()  # الرابط الذي أرسله المستخدم...Ссылка, отправленная пользователем
    msg = await update.message.reply_text("⏳ Загрузка аудио...")  # Бот отвечает, что началась загрузка аудио

    
    # Arabic: إعدادات التحميل
    # Russian: Настройки загрузки
    ydl_opts = {
        'format': 'bestaudio/best',  # أفضل جودة صوت...выбирается лучший доступный звук
        'outtmpl': os.path.join(TEMP_FOLDER, '%(title)s.%(ext)s'),  # مسار حفظ الملف..шаблон пути для сохранения файла
        'retries': 10,  # عدد المحاولات عند الفشل
        'continuedl': True,  # استكمال التحميل عند الانقطاع
        'concurrent_fragment_downloads': 4,  # تحميل أجزاء متعددة في نفس الوقت
        'fragment_retries': 5  # محاولات إعادة تحميل الأجزاء الفاشلة
    }

    try:
        
        # Arabic: تحميل الملف الصوتي من يوتيوب
        # Russian: Используется yt_dlp для скачивания информации и аудио
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=True)
            audio_file = ydl.prepare_filename(info)
            title = info.get("title", "Аудиофайл")  # اسم الملف للمستخدم بالروسية..заголовок видео, который будет отображаться в подписи к файлу.

        await msg.edit_text("✅ Отправка аудиофайла...")  # Обновляем сообщение, чтобы показать, что файл отправляется

        
        # Arabic: إرسال الملف بدون تحويل
        # Russian: Отправка файла без конвертации
        with open(audio_file, 'rb') as f:
            await update.message.reply_document(document=f, caption=title)  #Отправляем аудиофайл как документ (document)

        
        # Arabic: حذف الملف المؤقت بعد الإرسال
        # Russian: Удаление временного файла после отправки для экономии места
        os.remove(audio_file)
        await msg.edit_text("✅ Аудио отправлено и временный файл удалён.")  # Сообщение обновляется, чтобы уведомить пользователя

    except Exception as e:
        # Arabic: في حالة حدوث خطأ أثناء التحميل
        # Russian: Если возникает ошибка (например, неправильная ссылка), бот сообщает пользователю
        await msg.edit_text(f"❌ Ошибка при загрузке: {e}")  # للمستخدم فقط بالروسية


# Arabic: ربط الدوال وتشغيل البوت
# Russian: Подключение функций и запуск бота
app = ApplicationBuilder().token(BOT_TOKEN).build()
app.add_handler(CommandHandler("start", start))
app.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, handle_message))

print("🚀 Бот запущен...")  # رسالة للمطور فقط
app.run_polling()   #запускает бота в режиме ожидания сообщений

```
