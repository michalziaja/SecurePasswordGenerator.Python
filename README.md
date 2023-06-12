import random
import string

def generate_password(word, num_digits):
    password = ""
    mappings = {
        'a': ['@', '4', 'a', 'A'],
        'b': ['8', 'B'],
        'c': ['(', 'c', 'C'],
        'd': ['d', 'D'],
        'e': ['3', '€'],
        'f': ['F', 'f'],
        'g': ['g', 'G'],
        'h': ['H', '#'],
        'i': ['!', '1',],
        'j': ['J', 'j'],
        'k': ['k', 'K'],
        'l': ['l', 'L'],
        'm': ['M', 'm'],
        'n': ['n', 'N'],
        'o': ['0', 'O'],
        'p': ['P', 'p'],
        'q': ['Q', 'q'],
        'r': ['R', 'r'],
        's': ['$', '5', 'S', 's'],
        't': ['T', '+', 't'],
        'u': ['U', 'u'],
        'v': ['\/', 'V' 'v'],
        'w': ['VV', 'w', 'W'],
        'x': ['x', 'X'],
        'y': ['y', 'Y'],
        'z': ['7', 'z', 'Z']
    }

    if num_digits > 0:
        digits = ''.join(random.choice(string.digits) for _ in range(num_digits))
        password += digits + "."

    for char in word:
        if char.lower() in mappings:
            options = mappings[char.lower()]
            password += random.choice(options)
        else:
            password += char

    # Znak specjalny na końcu hasła
    if input("Czy dodać znak specjalny na końcu hasła? (Tak/Nie): ").lower() == "tak":
        password += random.choice([".", "!", "?"])

    return password


# Przykład użycia
input_word = input("Witam w generatorze unikalnych haseł na bazie słów \nWciśnij ENTER")
input_word = input("Wprowadź bazowe słowo: ")
input_num_digits = int(input("Podaj liczbę cyfr dołączonych do hasła: "))

password = generate_password(input_word, input_num_digits)
print("Hasło: " + password)
