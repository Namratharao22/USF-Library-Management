using System;
using System.Collections.Generic;


class Person
{
    public string Name { get; set; }
    public string Email { get; set; }
    public string ID { get; set; }

    public Person(string name, string email, string id)
    {
        Name = name;
        Email = email;
        ID = id;
    }
}


class Student : Person
{
    public string Major { get; set; }
    public int GraduationYear { get; set; }

    public Student(string name, string email, string id, string major, int graduationYear)
        : base(name, email, id)
    {
        Major = major;
        GraduationYear = graduationYear;
    }
}


class Staff : Person

{

    public string Position { get; set; }

    public string Department { get; set; }

    public Staff(string name, string email, string id, string position, string department)

        : base(name, email, id)

    {

        Position = position;

        Department = department;

    }

}
class Book
{
    public string Title { get; set; }
    public string Author { get; set; }
    public string ISBN { get; set; }
    public int AvailableCopies { get; set; }
 
    public Book(string title, string author, string isbn, int availableCopies)
    {
        Title = title;
        Author = author;
        ISBN = isbn;
        AvailableCopies = availableCopies;
    }
 
    public bool BorrowBook()
    {
        if (AvailableCopies > 0)
        {
            AvailableCopies--;
            return true;
        }
        return false;
    }
}
// Library class
class Library
{
    private List<Book> books = new List<Book>();
    private List<Person> patrons = new List<Person>();

    public void AddBook(Book book)
    {
        books.Add(book);
    }

    public void AddPatron(Person patron)
    {
        patrons.Add(patron);
    }

    public void DisplayBooks()
    {
        Console.WriteLine("Books in the Library:");
        foreach (var book in books)
        {
            Console.WriteLine($"Title: {book.Title}, Author: {book.Author}, ISBN: {book.ISBN}, Available Copies: {book.AvailableCopies}");
        }
        Console.WriteLine();
    }

    public void DisplayPatrons()
    {
        Console.WriteLine("Library Patrons:");
        foreach (var patron in patrons)
        {
            Console.WriteLine($"Name: {patron.Name}, Email: {patron.Email}, ID: {patron.ID}");
        }
        Console.WriteLine();
    }

    public void BorrowBook(Person patron, string bookTitle)
    {
        Book book = books.Find(b => b.Title == bookTitle);
        if (book != null && book.BorrowBook())
        {
            Console.WriteLine($"{patron.Name} borrowed \"{bookTitle}\".");
        }
        else
        {
            Console.WriteLine($"Sorry, \"{bookTitle}\" is not available.");
        }
    }
}

// Main method
class Program
{
    static void Main()
    {
        Library library = new Library();

        // Adding books
        library.AddBook(new Book("The Art of Data Strategy", "Liam Reynolds", "ISBN111", 4));
        library.AddBook(new Book("Business Insights with AI", "Olivia Carter", "ISBN222", 3));
        library.AddBook(new Book("Analytics in Action", "Nathan Brooks", "ISBN333", 6));

        // Adding students
        Student Namratha = new Student("Namratha", "Namratha@usf.edu", "S001", "Business Analytics", 2026);
        Student Ankitha = new Student("Ankitha", "Atripaty@usf.edu", "S002", "Information Systems", 2025);
        Student Vaishnavi = new Student("Vaishnavi", "vaishnavi@usf.edu", "S002", "Information Systems", 2025);
        Student Shubham = new Student("Subham", "subham@usf.edu", "S002", "Information Systems", 2025);
        library.AddPatron(Namratha);
        library.AddPatron(Ankitha);
        library.AddPatron(Vaishnavi);
        library.AddPatron(Shubham);

        // Adding staff
        Staff Shubhamgill = new Staff("Subham gill", "subamg@usf.edu", "ST001", "Librarian", "Library Services");
        library.AddPatron(Shubhamgill);

        // Display initial books and patrons
        library.DisplayBooks();
        library.DisplayPatrons();

        // Borrowing books
        library.BorrowBook(Namratha, "Business Insights with AI");
        library.BorrowBook(Ankitha, "Analytics in Action");

        // Display books after borrowing
        Console.WriteLine();
        library.DisplayBooks();
    }
} 
