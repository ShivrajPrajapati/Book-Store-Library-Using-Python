# Book-Store-Library-Using-Python


from utils import database
USER_CHOICE = """
-'a' to add a new book
-'l' to list all books
-'r' to mark a book as read
-'q' to quit
Your choice: """

def menu():
    database.create_book_table()
    user_input = input(USER_CHOICE)
    while user_input != 'q':
        if user_input == 'a':
            prompt_add_book()
        elif user_input == 'l':
            list_books() 
        elif user_input == 'r' :
            prompt_read_book() 
        elif user_input == 'd':
            prompt_delet_book()

        user_input = input(USER_CHOICE)

def prompt_add_book():
    name = input("Enter the new book name: ")
    author = input("Enter the new book author: ")

    database.add_book(name,author)

def list_books():
    for book in database.get_all_books():
        read = 'YES' if book['read'] else 'NO' 
        print(f"{book['namer']} by {book['author']} - Read: {read}") 

def prompt_read_book():
    name = input("Enter thye name of the book you just finished reading: ") 

    database.mark_book_as_read(name) 

def prompt_delet_book():
    name = input("Enter the name of the book you wish to delet: ")

    database.delet_book(name) 

menu()     
