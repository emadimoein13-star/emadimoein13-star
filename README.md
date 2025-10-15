import logging
from telegram import Update
from telegram.ext import ApplicationBuilder, ContextTypes, CommandHandler, MessageHandler, filters
import time

logging.basicConfig(
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
    level=logging.INFO
    
)

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await context.bot.send_message(chat_id=update.effective_chat.id, text="I'm  bot, please talk to me !")
    
    
    
    async def test(update: Update, context: ContextTypes.DEFAULT_TYPE):
    
    
        await update.message.reply_text("salam")
        
        
    async def robot1(update: Update, context: ContextTypes.DEFAULT_TYPE) -> int:
        text=update.message.text
        print(text)
        
        if text=='how are you':
            
        
            await update.message.reply_text("i m good and how are you?")
            
            
            if text=='saat':
                t=time.time()
                realtime=time.ctime(t)
                await update.message.reply_text(realtime)
            
            
    
    
    async def image(update: Update, context: ContextTypes.DEFAULT_TYPE) -> int:
    
        await update.message.reply_text("you photo")
    
    
    
    
    if __name__ == '__main__':
        application=ApplicationBuilder().token('8367197306:AAGdjIu6DFqC1q4SQ32PHCk5tLuqxrFqcAY').build()
        start_handler = CommandHandler('start', start)
        application.add_handler(start_handler)
        start_handler = CommandHandler('test', test)
        application.add_handler(start_handler)
        
        new_h=MessageHandler(filters=filters.TEXT ,callback= robot1)
        application.add_handler(new_h)
        
        application.run_polling()

