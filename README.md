class Book:
    def __init__(self, title, author, isbn):
        self.title = title
        self.author = author
        self.isbn = isbn
        self.is_borrowed = False

    def borrow(self):
        if not self.is_borrowed:
            self.is_borrowed = True
            return True
        return False

    def return_book(self):
        self.is_borrowed = False


class Patron:
    def __init__(self, name, patron_id):
        self.name = name
        self.patron_id = patron_id
        self.borrowed_books = []

    def borrow_book(self, book):
        self.borrowed_books.append(book)

    def return_book(self, book):
        if book in self.borrowed_books:
            self.borrowed_books.remove(book)


class Library:
    def __init__(self):
        self.books = []
        self.patrons = []

    def add_book(self, book):
        self.books.append(book)

    def register_patron(self, patron):
        self.patrons.append(patron)

    def borrow_book(self, patron, book):
        if book.borrow():
            patron.borrow_book(book)
            print(f"{patron.name} borrowed '{book.title}'")
        else:
            print("Book already borrowed.")

    def return_book(self, patron, book):
        book.return_book()
        patron.return_book(book)
        print(f"{patron.name} returned '{book.title}'")


library = Library()

book1 = Book("Python Basics", "John Smith", "101")
book2 = Book("OOP in Python", "Jane Doe", "102")

library.add_book(book1)
library.add_book(book2)

patron = Patron("Rahul", 1)
library.register_patron(patron)

library.borrow_book(patron, book1)
library.return_book(patron, book1)
