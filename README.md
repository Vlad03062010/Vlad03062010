import telebot
from telebot import types

bot = telebot.TeleBot('6720844774:AAFe-gtZO1IXJjpWmG4F2-VVxVHmsM1lQfI')


@bot.message_handler(commands=['start', 'test'])
def start(message):
    if message.text == '/test':
        bot.send_message(message.chat.id, "Ты человек?")
        keyboard = types.InlineKeyboardMarkup()
        key_yes = types.InlineKeyboardButton(text='Да', callback_data='yes')
        key_no = types.InlineKeyboardButton(text='Нет', callback_data='no')
        keyboard.add(key_yes, key_no)
        bot.send_message(message.chat.id, text='Ответь на вопрос', reply_markup=keyboard)
    else:
        bot.send_message(message.chat.id, 'Привет! Хочешь пройти тест на внимательность? Тогда нажми на /test')


@bot.callback_query_handler(func=lambda call: True)
def callback_worker(call):
    if call.data == "yes":
        keyboard = types.InlineKeyboardMarkup()
        key_1 = types.InlineKeyboardButton(text='0', callback_data='second')
        keyboard.add(key_1)
        key_2 = types.InlineKeyboardButton(text='242', callback_data='second')
        keyboard.add(key_2)
        key_3 = types.InlineKeyboardButton(text='56', callback_data='second')
        keyboard.add(key_3)
        bot.send_message(call.message.chat.id, text='Сколько будет 54+2', reply_markup=keyboard)
    elif call.data == "second":
        keyboard = types.InlineKeyboardMarkup()
        key_1 = types.InlineKeyboardButton(text='87', callback_data='third')
        keyboard.add(key_1)
        key_2 = types.InlineKeyboardButton(text='54', callback_data='third')
        keyboard.add(key_2)
        key_3 = types.InlineKeyboardButton(text='42', callback_data='third')
        keyboard.add(key_3)
        bot.send_message(call.message.chat.id, text='Сколько будет 8+23*2', reply_markup=keyboard)
    elif call.data == "third":
        keyboard = types.InlineKeyboardMarkup()
        key_1 = types.InlineKeyboardButton(text='8', callback_data='fourth')
        keyboard.add(key_1)
        key_2 = types.InlineKeyboardButton(text='76', callback_data='fourth')
        keyboard.add(key_2)
        key_3 = types.InlineKeyboardButton(text='30', callback_data='fourth')
        keyboard.add(key_3)
        bot.send_message(call.message.chat.id, text='Сколько будет 24*2/6', reply_markup=keyboard)
    elif call.data == "fourth":
        keyboard = types.InlineKeyboardMarkup()
        key_1 = types.InlineKeyboardButton(text='-21', callback_data='fifth')
        keyboard.add(key_1)
        key_2 = types.InlineKeyboardButton(text='-25', callback_data='fifth')
        keyboard.add(key_2)
        key_3 = types.InlineKeyboardButton(text='25', callback_data='fifth')
        keyboard.add(key_3)
        bot.send_message(call.message.chat.id, text='Сколько будет -23-2', reply_markup=keyboard)
    elif call.data == "fifth":
        keyboard = types.InlineKeyboardMarkup()
        key_1 = types.InlineKeyboardButton(text='-24', callback_data='sixth')
        keyboard.add(key_1)
        key_2 = types.InlineKeyboardButton(text='24', callback_data='sixth')
        keyboard.add(key_2)
        key_3 = types.InlineKeyboardButton(text='21', callback_data='sixth')
        keyboard.add(key_3)
        bot.send_message(call.message.chat.id, text='Сколько будет 23+(-2)', reply_markup=keyboard)
    elif call.data == "sixth":
        keyboard = types.InlineKeyboardMarkup()
        key_1 = types.InlineKeyboardButton(text='230', callback_data='seventh')
        keyboard.add(key_1)
        key_2 = types.InlineKeyboardButton(text='232', callback_data='seventh')
        keyboard.add(key_2)
        key_3 = types.InlineKeyboardButton(text='228', callback_data='seventh')
        keyboard.add(key_3)
        bot.send_message(call.message.chat.id, text='Сколько будет 230-(-2)', reply_markup=keyboard)
    elif call.data == "seventh":
        keyboard = types.InlineKeyboardMarkup()
        key_1 = types.InlineKeyboardButton(text='2.5', callback_data='eighth')
        keyboard.add(key_1)
        key_2 = types.InlineKeyboardButton(text='4.5', callback_data='eighth')
        keyboard.add(key_2)
        key_3 = types.InlineKeyboardButton(text='4.3', callback_data='eighth')
        keyboard.add(key_3)
        bot.send_message(call.message.chat.id, text='Сколько будет 2.3+2', reply_markup=keyboard)
    elif call.data == "eighth":
        keyboard = types.InlineKeyboardMarkup()
        key_1 = types.InlineKeyboardButton(text='25', callback_data='ninth')
        keyboard.add(key_1)
        key_2 = types.InlineKeyboardButton(text='0', callback_data='ninth')
        keyboard.add(key_2)
        key_3 = types.InlineKeyboardButton(text='11.5', callback_data='ninth')
        keyboard.add(key_3)
        bot.send_message(call.message.chat.id, text='Сколько будет 23/2', reply_markup=keyboard)
    elif call.data == "ninth":
        keyboard = types.InlineKeyboardMarkup()
        key_1 = types.InlineKeyboardButton(text='46', callback_data='tenth')
        keyboard.add(key_1)
        key_2 = types.InlineKeyboardButton(text='48', callback_data='tenth')
        keyboard.add(key_2)
        key_3 = types.InlineKeyboardButton(text='232', callback_data='tenth')
        keyboard.add(key_3)
        bot.send_message(call.message.chat.id, text='Сколько будет 23*2', reply_markup=keyboard)
    elif call.data == 'tenth':
        bot.send_message(call.message.chat.id, text='Поздравляю! Ты прошел на все 100 из 100 баллов')


def prank(message):
    if message.text.lower() == 'eleventh':
        bot.send_message(message.chat.id, "Люблю шутников!")


bot.polling(none_stop=True, interval=0)
