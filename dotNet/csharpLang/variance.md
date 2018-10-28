# Covariance & Contravariance

Variance refers to how subtyping between more complex types relates to subtyping between their components.
For instance, if Rectangle class inhereits from Shape class, then how do generic datatypes, delegates and assignment relate between these two types. Regarding this, we have two concepts


## Covariance 
Covariance is when a more generic type (`object`) can be assigned a less generic type (`string`). It is denoted by `out T` in C#, where `T` is the type itself. 

**Analogy:**
`out` as in more outward i.e. out of `T` or more generic than `T` can be assigned less generic type.

## Contravariance 
Contravariance is reverse of Covariance and is when a less generic type (`string`) can be assigned a more generic type (`object`). It is denoted by `in T` keyword in C#, where `T` is the type itself. 

**Analogy:** `in` as in more inward i.e. less than `T` or less generic than `T` can be assigned more generic type

## Example

```
public class Variance
{
    public void Covariance()
    {
        IEnumerable<Rectangle> rectangles = new List<Rectangle>();
        IEnumerable<Shape> shapes = new List<Shape>();

        shapes = rectangles; //covariance

        //Following assignement is not possible imlicitly due to no contravariance
        //rectangles = shapes; 
    }

    public void Contravariance()
    {
        Shape s = new Shape();
        Action<Shape> shapeAction = ShapeAction;
        shapeAction(s);


        Action<Rectangle> recAction = ShapeAction; //contravariance
        recAction(new Rectangle());

        //Following assigment is not possible implicitly due to no convariance
        //shapeAction = recAction; 
    }

    void ShapeAction(Shape s)
    {
        Console.WriteLine(s.ToString());
    }
}

public class Shape
{
    protected int Area;
    protected string Color;
}

public class Rectangle : Shape 
{
    int length;
    int width;

    public Rectangle()
    {
        Color = "red";
    }
}
```