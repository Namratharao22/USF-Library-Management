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
