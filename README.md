# Project-Text-Analyzer

TEXTS = ['''
Situated about 10 miles west of Kemmerer, Fossil Butte is a ruggedly impressive topographic feature that rises sharply 
some 1000 feet above Twin Creek Valley to an elevation of more than 7500 feet above sea level. The butte is located just 
north of US 30N and the Union Pacific Railroad, which traverse the valley. ''',

'''At the base of Fossil Butte are the bright red, purple, yellow and gray beds of the Wasatch 
Formation. Eroded portions of these horizontal beds slope gradually upward from the valley floor 
and steepen abruptly. Overlying them and extending to the top of the butte are the much steeper 
buff-to-white beds of the Green River Formation, which are about 300 feet thick.''',

'''The monument contains 8198 acres and protects a portion of the largest deposit of freshwater fish 
fossils in the world. The richest fossil fish deposits are found in multiple limestone layers, which lie some 
100 feet below the top of the butte. The fossils represent several varieties of perch, as well as 
other freshwater genera and herring similar to those in modern oceans. Other fish such as paddlefish, 
garpike and stingray are also present.'''
]

Registered_User = ('Bob', 'Ann', 'Mike', 'Liz')
Password_User = ('123', 'pass123', 'password123', 'pass123')
Dash = 40 * '-'

Name = input('USER NAME: ')
Password = input('PASSWORD: ')
print(Dash)

# Searching for existing user from Registered users
if Name not in Registered_User:
    print('The user is not registered')
    exit()

print('Welcome to the app,', Name, 'We have', len(TEXTS), 'texts to be analyzed.')
print(Dash)

Selection = input('Enter a number btw. 1 and 3 to select: ')
print(Dash)
Selected_text = TEXTS[int(Selection) - 1].strip()

# Asking a user to select the text
if Selection.isalpha() or int(Selection) < 1 or int(Selection) > 3:
    print('Please, enter a number btw. 1 and 3 to select')
    exit()

words = Selected_text.split(" ")
print("There are", len(words), "words in the selected text.")


count_capital_letters = 0
count_capital_words = 0
count_lower_words = 0
count_numbers = 0
sum_numbers = 0

for word in words:
    if len(word) > 0 and word[0].isupper():
        count_capital_letters += 1
    if word.isupper() and word.isalpha():
        count_capital_words += 1
    if word.islower():
        count_lower_words += 1
    if word.isdigit():
        count_numbers += 1
        sum_numbers += int(word)

print("There are", count_capital_letters, "titlecase words.")
print("There are", count_capital_words, "uppercase words.")
print("There are", count_lower_words, "lowercase words.")
print("There are", count_numbers, "numeric strings.")
print("The sum of all the numbers:", sum_numbers)
print(Dash)
print("LEN |  OCCURENCES        |NR.")
print(Dash)

for index in range(len(max(words, key=len))):
    len_word = index + 1
    count_word = 0

    for word in words:
        if len(word) == len_word:
            count_word += 1

    star_result = " "

    for star in range(15):
        if star < count_word:
            star_result += "*"
        else:
            star_result += " "

    print(len_word, "  |", star_result, "  |", count_word)




