numbers = list(map(int, input("Enter numbers: ").split()))

for i in range(len(numbers)):
    for j in range(i + 1, len(numbers)):
        if numbers[i] > numbers[j]:
            numbers[i], numbers[j] = numbers[j], numbers[i]

print("Sorted numbers:", numbers)



text = input("Enter a word: ")

frequency = {}

for char in text:
    frequency[char] = frequency.get(char, 0) + 1

for char, count in frequency.items():
    print(char, ":", count)




def largest_word(sentence):
    words = sentence.split()
    largest = words[0]

    for word in words:
        if len(word) > len(largest):
            largest = word

    return largest

text = input("Enter sentence: ")

print("Largest word:", largest_word(text))



# def find_missing(numbers):
    n = len(numbers) + 1
    expected = n * (n + 1) // 2
    return expected - sum(numbers)

numbers = list(map(int, input("Enter numbers: ").split()))

print("Missing number:", find_missing(numbers))
