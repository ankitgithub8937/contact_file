# contact_file
this is calculated programme
def add_contact():
    name = input("Enter name: ")
    phone = input("Enter phone number: ")
    email = input("Enter email: ")
    
    with open("contacts.txt", "a") as file:
        file.write(f"{name},{phone},{email}\n")
    print("Contact added successfully.")


def view_contacts():
    try:
        with open("contacts.txt", "r") as file:
            contacts = file.readlines()
            if not contacts:
                print("No contacts found.")
                return
            print("\nContacts:")
            for line in contacts:
                name, phone, email = line.strip().split(",")
                print(f"Name: {name}, Phone: {phone}, Email: {email}")
    except FileNotFoundError:
        print("No contacts found. Add some first.")


def search_contacts():
    keyword = input("Enter name or phone/email to search: ").lower()
    found = False
    try:
        with open("contacts.txt", "r") as file:
            for line in file:
                if keyword in line.lower():
                    name, phone, email = line.strip().split(",")
                    print(f"Found -> Name: {name}, Phone: {phone}, Email: {email}")
                    found = True
        if not found:
            print("No matching contact found.")
    except FileNotFoundError:
        print("No contacts found.")


def main():
    while True:
        print("\n--- Contact Book ---")
        print("1. Add Contact")
        print("2. View Contacts")
        print("3. Search Contact")
        print("4. Exit")

        choice = input("Choose an option (1-4): ")
        if choice == "1":
            add_contact()
        elif choice == "2":
            view_contacts()
        elif choice == "3":
            search_contacts()
        elif choice == "4":
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Try again.")

if _name_ == "_main_":
    main()
