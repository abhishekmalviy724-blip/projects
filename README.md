# def find_missing(numbers):
    n = len(numbers) + 1
    expected = n * (n + 1) // 2
    return expected - sum(numbers)

numbers = list(map(int, input("Enter numbers: ").split()))

print("Missing number:", find_missing(numbers))
