balance = 5000
pin = 1234

user_pin = int(input("PIN enter karo: "))

if user_pin == pin:
    print("\n1. Balance Check")
    print("2. Deposit")
    print("3. Withdraw")

    choice = int(input("\nApna choice select karo: "))

    if choice == 1:
        print("Your balance is ₹", balance)

    elif choice == 2:
        amount = float(input("Deposit amount: ₹"))

        if amount > 0:
            balance += amount
            print("Deposit successful!")
            print("New balance: ₹", balance)
        else:
            print("Invalid amount!")

    elif choice == 3:
        amount = float(input("Withdraw amount: ₹"))

        if amount <= 0:
            print("Invalid amount!")
        elif amount > balance:
            print("Insufficient balance!")
        else:
            balance -= amount
            print("Withdrawal successful!")
            print("Remaining balance: ₹", balance)

    else:
        print("Invalid choice!")

else:
    print("❌ Wrong PIN!")



# def word_frequency(text):
#     new={}
#     for i in text.split():
#         if i in new:
#             new[i]+=1
#         else:
#             new[i]=1
#     return new
# print(word_frequency("Python is great and Python is easy"))

# def group_anagrams(words):
#     new=[]
#     for i in words:
#         for j in new:
#             if sorted(i) == sorted(j[0]):
#                 j.append(i)
#                 break
#         else:
#             new.append([i])
#     return new
# print(group_anagrams(["eat", "tea", "tan", "ate", "nat", "bat"]))

# a=[1, [2, [3, 4], 5], 6, [7, 8]]
# new=[]
# for i in a:
#     for j in i:
#         print(j)





def sum_digits(n):
    if n == 0:
        return 0
    return n % 10 + sum_digits(n // 10)

num = int(input("Enter number: "))

print("Sum of digits:", sum_digits(num))



text = input("Enter a sentence: ")

words = text.lower().split()
longest = ""

for word in words:
    if len(word) > len(longest):
        longest = word

print("Longest word:", longest)
print("Length:", len(longest))


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
