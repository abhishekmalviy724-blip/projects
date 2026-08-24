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
