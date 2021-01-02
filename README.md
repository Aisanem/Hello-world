# TelegramBot

import telebot
from config import keys, TOKEN
from utils import ConvertionException, Cryptoconverter

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
        for key in keys.keys()
        text = '\n'.join((text, key,))
    bot.reply_to(message, text)


@bot.message_handler(content_types=['text', ])
def convert(message: telebot.types.Message):
    values = massage.text.split(' ')
    values = list(map(str.lower, value))
    try:
       if len(values) != 3:
          raise ConvertionException('Слишком много параметров.')
       quotes, base, amount = values
       total_base = CryptoConverter.convert(quote, base, amount)
    except ConverterException as e:
       bot.reply_to(massage, f'Не удалось обработать команду\n{e}')
    except Exception as e:
       bot.reply_to(massage, f'Не удалось обработатькоманду\n{e}')
    else:
       text = f'Цена{amount} {quote} в {base} -- {total_base}'
       bot.reply_to(message.chat.id, text)

 bot.polling(non_stop=True, interval=0)
