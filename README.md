# python-practical

# ***Practical 1***

#**Program to find roots of a quadratic equation**

import cmath

a=int(input('Enter the value of a:'))

b=int(input('Enter the value of b:'))


c=int(input('Enter the value of c:'))


#to find a discriminant

d=(b**2)-(4*a*c)

print('The value of discriminant is:',d)

# ***Practical 2***
def is_prime(num):
    if num < 2:
        return False
    for i in range(2, int(num**0.5) + 1):
        if num % i == 0:
            return False
    return True

def generate_primes_till_n(n):
    primes = [num for num in range(2, n+1) if is_prime(num)]
    return primes

def generate_first_n_primes(n):
    primes = []
    num = 2
    while len(primes) < n:
        if is_prime(num):
            primes.append(num)
        num += 1
    return primes

# Test the functions
number = int(input("Enter a number (n): "))

# a. Check if 'n' is prime
if is_prime(number):
    print(f"{number} is a prime number.")
else:
    print(f"{number} is not a prime number.")

# b. Generate all prime numbers till 'n'
primes_till_n = generate_primes_till_n(number)
print(f"Prime numbers till {number}: {primes_till_n}")

# c. Generate first 'n' prime numbers
first_n_primes = generate_first_n_primes(number)
print(f"First {number} prime numbers: {first_n_primes}")

# ***Practical 3***
def print_pyramid(rows):
    for i in range(1, rows + 1):
        print(' ' * (rows - i) + '*' * (2 * i - 1))

def print_reverse_pyramid(rows):
    for i in range(rows, 0, -1):
        print(' ' * (rows - i) + '*' * (2 * i - 1))

# Number of rows for the pyramid
pyramid_rows = 5

# Print the pyramid
print("Pyramid:")
print_pyramid(pyramid_rows)

# Number of rows for the reverse pyramid
reverse_pyramid_rows = 5

# Print the reverse pyramid
print("\nReverse Pyramid:")
print_reverse_pyramid(reverse_pyramid_rows)

# ***Practical 4***
def char_analysis(char):
    if char.isalpha():
        if char.isupper():
            print(f"The character '{char}' is an uppercase letter.")
        else:
            print(f"The character '{char}' is a lowercase letter.")
    elif char.isdigit():
        digit_name = {'0': 'ZERO', '1': 'ONE', '2': 'TWO', '3': 'THREE', '4': 'FOUR', '5': 'FIVE',
                      '6': 'SIX', '7': 'SEVEN', '8': 'EIGHT', '9': 'NINE'}
        print(f"The character '{char}' is a numeric digit and its name is {digit_name[char]}.")
    else:
        print(f"The character '{char}' is a special character.")

# Take user input
character = input("Enter a character: ")

# Analyze the character
char_analysis(character)

# ***Practical 5***
def frequency_of_character(input_string, char):
    return input_string.count(char)

def replace_character(input_string, old_char, new_char):
    return input_string.replace(old_char, new_char)

def remove_first_occurrence(input_string, char):
    return input_string.replace(char, '', 1)

def remove_all_occurrences(input_string, char):
    return input_string.replace(char, '')

# Take user input
input_string = input("Enter a string: ")

# a. Find the frequency of a character in a string
char_to_find = input("Enter a character to find its frequency: ")

frequency = frequency_of_character(input_string, char_to_find)

print(f"The frequency of '{char_to_find}' in the string is: {frequency}")

# b. Replace a character by another character in a string
old_char = input("Enter the character to be replaced: ")
new_char = input("Enter the new character: ")
string_after_replace = replace_character(input_string, old_char, new_char)
print(f"The string after replacing '{old_char}' with '{new_char}': {string_after_replace}")

# c. Remove the first occurrence of a character from a string
char_to_remove_first = input("Enter the character to be removed (first occurrence): ")
string_after_remove_first = remove_first_occurrence(input_string, char_to_remove_first)
print(f"The string after removing the first occurrence of '{char_to_remove_first}': {string_after_remove_first}")

# d. Remove all occurrences of a character from a string
char_to_remove_all = input("Enter the character to be removed (all occurrences): ")
string_after_remove_all = remove_all_occurrences(input_string, char_to_remove_all)
print(f"The string after removing all occurrences of '{char_to_remove_all}': {string_after_remove_all}")

# ***Practical 6***
def swap_first_n_characters(str1, str2, n):
    if n > min(len(str1), len(str2)):
        print("Cannot swap first", n, "characters as one or both strings are shorter.")
        return

    new_str1 = str2[:n] + str1[n:]
    new_str2 = str1[:n] + str2[n:]

    return new_str1, new_str2

# Take user input
string1 = input("Enter the first string: ")
string2 = input("Enter the second string: ")
n = int(input("Enter the number of characters to swap: "))

# Perform the swap
result1, result2 = swap_first_n_characters(string1, string2, n)

# Display the result
if result1 and result2:
    print(f"After swapping the first {n} characters:")
    print("String 1:", result1)
    print("String 2:", result2)

# ***Practical 7***
def find_occurrences_indices(main_string, sub_string):
    indices = []
    index = main_string.find(sub_string)

    while index != -1:
        indices.append(index)
        index = main_string.find(sub_string, index + 1)

    return indices if indices else -1

# Example usage
main_str = "abababab"
sub_str = "ab"

result = find_occurrences_indices(main_str, sub_str)

if result == -1:
    print(f"The substring '{sub_str}' is not present in the main string.")
else:
    print(f"The substring '{sub_str}' occurs at indices: {result}")

 # ***Practical 8***
 Using 'for' loop:
      def cubes_of_even_numbers_for_loop(input_list):
    result = []
    for element in input_list:
        if isinstance(element, int) and element % 2 == 0:
            result.append(element ** 3)
    return result
Using List Comprehension:
     def cubes_of_even_numbers_list_comprehension(input_list):
    return [element ** 3 for element in input_list if isinstance(element, int) and element % 2 == 0]

# ***Practical 9***
def analyze_file(file_path):
    with open(file_path, 'r') as file:
        # a. Print the total number of characters, words, and lines in the file
        content = file.read()
        total_characters = len(content)
        total_words = len(content.split())
        total_lines = content.count('\n') + 1

        print(f"a. Total characters: {total_characters}")
        print(f"   Total words: {total_words}")
        print(f"   Total lines: {total_lines}")

        # b. Calculate the frequency of each character in the file
        character_frequency = {}
        for char in content:
            if char.isalnum():
                char = char.lower()  # Consider case-insensitive
                character_frequency[char] = character_frequency.get(char, 0) + 1

        print("\nb. Frequency of each character:")
        for char, count in character_frequency.items():
            print(f"   {char}: {count}")

        # c. Print the words in reverse order
        words = content.split()
        reversed_words = ' '.join(reversed(words))
        print("\nc. Words in reverse order:")
        print(reversed_words)

        # d. Copy even lines to 'File1' and odd lines to 'File2'
        with open('File1.txt', 'w') as file1, open('File2.txt', 'w') as file2:
            lines = content.splitlines()
            for i, line in enumerate(lines, start=1):
                if i % 2 == 0:
                    file1.write(line + '\n')
                else:
                    file2.write(line + '\n')

# ***Practical 10***
import math

class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def print_coordinates(self):
        print(f"Coordinates: ({self.x}, {self.y})")

    def distance(self, other_point):
        dx = self.x - other_point.x
        dy = self.y - other_point.y
        return math.sqrt(dx**2 + dy**2)

# Print coordinates of the points
point1.print_coordinates()
point2.print_coordinates()

# Calculate and print the distance between the points
distance_between_points = point1.distance(point2)
print(f"Distance between the points: {distance_between_points}")

# ***Practical 11***

def create_cubes_dictionary():
    cubes_dict = {num: num ** 3 for num in range(1, 6)}
    return cubes_dict
# ***Practical 12***
# Given tuple
t1 = (1, 2, 5, 7, 9, 2, 4, 6, 8, 10)

# a) Print half the values of the tuple in one line and the other half in the next line.
half_length = len(t1) // 2
print("a) Half the values of the tuple in one line:")
print(t1[:half_length])
print("   The other half in the next line:")
print(t1[half_length:])

# b) Print another tuple whose values are even numbers in the given tuple.
even_numbers_tuple = tuple(num for num in t1 if num % 2 == 0)
print("\nb) Tuple of even numbers in the given tuple:")
print(even_numbers_tuple)

# c) Concatenate a tuple t2=(11, 13, 15) with t1.
t2 = (11, 13, 15)
concatenated_tuple = t1 + t2
print("\nc) Concatenated tuple of t1 and t2:")
print(concatenated_tuple)

# d) Return maximum and minimum value from this tuple
max_value = max(t1)
min_value = min(t1)
print("\nd) Maximum value in the tuple:", max_value)
print("   Minimum value in the tuple:", min_value)

# ***Practical 13***
def validate_name(name):
    for char in name:
        if not char.isalpha():
            raise ValueError("Name should only contain alphabetic characters.")

# Example usage
try:
    user_input = input("Enter your name: ")
    validate_name(user_input)
    print("Entered name:", user_input)
except ValueError as ve:
    print(f"Error: {ve}")


