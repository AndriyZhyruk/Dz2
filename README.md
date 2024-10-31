using System;

class GradeBook
{
    public delegate void GradeAddedEventHandler(int grade);
    public event GradeAddedEventHandler GradeAdded;

    public void AddGrade(int grade)
    {
        Console.WriteLine("Added grade: " + grade);
        GradeAdded?.Invoke(grade);
    }
}

class GradeListener
{
    public void OnGradeAdded(int grade)
    {
        Console.WriteLine("New grade received: " + grade);
    }
}

class Program
{
    public static void Main()
    {
        GradeBook gradeBook = new GradeBook();
        GradeListener gradeListener = new GradeListener();

        gradeBook.GradeAdded += gradeListener.OnGradeAdded;

        gradeBook.AddGrade(85);
        gradeBook.AddGrade(90);
    }
}
