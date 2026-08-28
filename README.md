numbers = list(map(int, input("Enter numbers: ").split()))

duplicates = []

for i in range(len(numbers)):
    count = 0

    for j in range(len(numbers)):
        if numbers[i] == numbers[j]:
            count += 1

    if count > 1 and numbers[i] not in duplicates:
        duplicates.append(numbers[i])

print("Duplicate numbers:", duplicates)



def LMS(Book,User_Name,User_Id,Status):
    Books = ["Python", "SQL", "Machine Learning", "Excel"]
    Boosk = {"B101" :{
        "Name":"python",
        "Author":"Gito",
        "status":"Av"
    }}
    User = {"Abhishek","Rahul","Sanvi","Mahi"}
    Category = {"programming","Database","AI","PHP"}
    Library_config = ("Central Library", 5)
    while True:
        print("\n1. Book")
        print("2. User Name")
        print("3. User ID") 
        print("4. Status")
        print("5. Exit")
        
        choice = int(input("Enter Choice!"))
        if choice == 1:
                print (Book)
        elif choice == 2:
                print(User_Name)
        elif choice == 3:
                print(User_Id)
        elif choice == 4:
                print(Status)
        elif choice == 5:
            print("Thank You!")
            break
        else:
            print("Invalid Choice")
    
        
obj=LMS(["A","B",""],"Abhihek","763URYB","Active")






numbers = list(map(int, input("Enter numbers: ").split()))

for i in range(len(numbers)):
    count = 0

    for j in range(len(numbers)):
        if numbers[i] == numbers[j]:
            count += 1

    if count == 1:
        print("First unique number:", numbers[i])
        break



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
