# project
user= {"Sanvi":123}
while True:
    print("Enter Your Prefrance")
    print('1. Login')
    print('2. Register')
    print('3. Forgot Password')
    print('4. Exit')        
    choice=int(input("Enter Choice"))
    if choice == 1:
        Username=input("Enter Username:- ")
        if Username=="Abhishek":
            Passwordd=int(input("Enter Password:- "))
            if Username=="Abhishek" and Passwordd==000:
                print("Login Successfull")
            else:
                print("Wrong Password")
        else:
            print("User not found!")
    if choice==2:
        regi_Username=input("Enter Username:-")
        if regi_Username in user:
            print("Already Exists")
        else:
            regi_Password=input("Enter Password:-")
            user[regi_Username]=regi_Password
        print("Registration Successfull.")    
    if choice==3:
        break
