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
// Book class
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
 
