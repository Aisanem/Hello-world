# TelegramBot

import telebot
from config import keys, TOKEN
from bot2 import ConvertionException, Cryptoconverter

bot = telebot.Telebot(TOKEN)


@bot.message_handler(commands=['start', 'help'])
def help(message: telebot.types.Message):
    text = 'Чтобы начать работу введите команду боту в следующем формате:\n<имя валюты> \ \
<в какую валюту превести> \
<колличество преведенной валюты>\nУвидеть список всех доступных валют: /values'
    bot.reply_to(message, text)


@bot.message_handler(commads=['values'])
def values(message: telebot.types.Message):
    text = 'Доступные валюты:'
