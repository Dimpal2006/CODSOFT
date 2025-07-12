# CODSOFT
'''__________________TASK 2 - CALCULATOR__________________'''



class Solution:
    def calculate(self, s: str) -> int:
        i=0
        
        cur = prev = res = 0
        cur_operation ="+"

        while i < len(s):
            cur_char = s[i]
            if cur_char.isdigit():
                while i < len(s) and s[i].isdigit():
                    cur = cur * 10 + int(s[i])
                    i += 1
                i -= 1
                if cur_operation == "+":
                    res += cur
                    prev = cur
                elif cur_operation == "-":
                    res -= cur 
                    prev = -cur
                elif cur_operation =="*":
                    res -= prev
                    res += prev * cur
                    prev = cur * prev
                else:
                    res -= prev
                    res += int(prev / cur)
                    prev = int(prev / cur)
                cur = 0
            elif cur_char != " ":
                cur_operation = cur_char
            i += 1
        return res  

        

'''________________TASK 3 - PASSWORD GENERATOR________________'''




import random
import string

def generate_password(length):
    characters = string.ascii_letters + string.digits + string.punctuation
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

if __name__=="__main__":
    password_length = int(input("Enter the password length: "))
    
    if(password_length < 6):
        print("Password length should be at least 6 characters")
    else:
        random_password = generate_password(password_length)
        print("Your random password is: ",random_password)



'''__________________TASK 4 - ROCK-PAPER-SCISSORS GAME__________________'''



def computer_choice():
    return random.choice(['rock','paper','scissors'])
def game(player, computer):
    if player==computer:
        return "It's a Tie!!"
    if (player=='rock' and computer=='paper') or (player=='paper' and computer=='scissors') or (player=='scissors' and computer=='rock'):
        return "Computer Wins"
    return "Player Wins"
while True:
    print("Welcome to the game , type 'exit' to get out of this game!Thank You")
    player_choice=input("Enter your choice from {rock , paper , scissors}:").lower()
    if player_choice=='exit':
        print("GoodBye !")
        break
    elif player_choice not in ['rock','paper','scissors']:
        print("Invalid choice ! Try again...")
        continue
    computer = computer_choice()
    print("computer chose : ",computer)
    result = game(player_choice, computer)
    print(result)



'''__________________TASK 5 - CONTACT BOOK__________________'''

  
  
  
  class Contact:
    def __init__(self, name, phone_number, email):
        self.name = name
        self.phone_number = phone_number
        self.email = email

class ContactBook:
    def __init__(self):
        self.contacts = []

    def add_contact(self):
        name = input("Enter name: ")
        phone_number = input("Enter phone number: ")
        email = input("Enter email: ")
        contact = Contact(name, phone_number, email)
        self.contacts.append(contact)
        print("Contact added successfully!")

    def view_contact_list(self):
        if not self.contacts:
            print("No contacts in the contact book.")
        else:
            for index, contact in enumerate(self.contacts, start=1):
                print(f"Contact {index}:")
                print(f"Name: {contact.name}")
                print(f"Phone Number: {contact.phone_number}")
                print(f"Email: {contact.email}")
                print("------------------------")

    def search_contact(self):
              name = input("Enter name to search: ")
        found_contacts = [contact for contact in self.contacts if contact.name.lower() == name.lower()]
        if found_contacts:
            for index, contact in enumerate(found_contacts, start=1):
                print(f"Contact {index}:")
                print(f"Name: {contact.name}")
                print(f"Phone Number: {contact.phone_number}")
                print(f"Email: {contact.email}")
                print("------------------------")
        else:
            print("Contact not found.")

    def update_contact(self):
        name = input("Enter name of contact to update: ")
        for contact in self.contacts:
            if contact.name.lower() == name.lower():
                contact.name = input("Enter new name: ") or contact.name
                contact.phone_number = input("Enter new phone number: ") or contact.phone_number
                contact.email = input("Enter new email: ") or contact.email
                print("Contact updated successfully!")
                return
        print("Contact not found.")

    def delete_contact(self):
        name = input("Enter name of contact to delete: ")
        for contact in self.contacts:
            if contact.name.lower() == name.lower():
                self.contacts.remove(contact)
                print("Contact deleted successfully!")
                return
        print("Contact not found.")

def main():
    contact_book = ContactBook()
    while True:
        print("\nContact Book Menu:")
        print("1. Add Contact")
        print("2. View Contact List")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")
        choice = input("Enter your choice: ")
        if choice == "1":
            contact_book.add_contact()
        elif choice == "2":
            contact_book.view_contact_list()
        elif choice == "3":
            contact_book.search_contact()
        elif choice == "4":
            contact_book.update_contact()
        elif choice == "5":
            contact_book.delete_contact()
        elif choice == "6":
            print("Exiting contact book.")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
