# Reto 5 POO
### Katherine Restrepo

#### Create a package with all code of class Shape, this exersice should be conducted in two ways:
#### A unique module inside of package Shape


```python
class Point:
  definition: str = "Entidad geometrica abstracta que representa una ubicación en un espacio."
  def __init__(self, x: int, y: int):
    self.x = x
    self.y = y

  def legible(self):
     return f"({self.x},{self.y})"
  
  def compute_distance(self, punto:"Point"):
     return ((punto.x-self.x)**2 + (punto.y-self.y)**2)**1/2

class Line:
    def __init__(self, lenght:float,start_point: Point , end_point: Point):
        self.length=lenght
        self.start_point=start_point
        self.end_point=end_point

class Shape():
    def __init__(self, is_regular:bool):
      self.is_regular=is_regular
      
    def vertices(self,lista:list[Point]):
      self.lista=lista
      
    def edges(self,lista_e:list[Line]):
       self.lista_e=lista_e
    
    def inner_angles(self,lista_a:list[float]):
       self.lista_a=lista_a

    def compute_area(self):
       pass

    def compute_perimeter(self):
       pass

    def compute_inner_angles(self):
       pass
```
#### Modulo Shape
```python
from Shape.shape import Shape

class Rectangle(Shape):
    def __init__(self, ancho:float, alto:float):
        super().__init__()
        self.ancho=ancho
        self.alto= alto
    
    def compute_area(self):
        return self.ancho* self.alto
    
    def compute_perimeter(self):
        return 2*self.alto+ 2*self.ancho
    
    def compute_inner_angles(self):
       return 360/4
    
class Square(Rectangle):
    def __init__(self, lado:float):
        super().__init__()
        self.lado=lado
    
    def compute_area(self)-> float:
        return self.lado**2
    
    def compute_perimeter(self)-> float:
        return 4* self.lado
    
    def compute_inner_angles(self):
       return super().compute_inner_angles()
    
class Triangle(Shape):
    def __init__(self, base:float, altura:float):
      super().__init__()
      self.base=base
      self.altura=altura
    
    def compute_area(self):
       return self.base*self.altura/2

    def compute_perimeter(self):
       pass

    def compute_inner_angles(self):
       pass
    
class Equilatero(Triangle):
    def __init__(self, lado,base,altura):
      super().__init__()
      self.lado=lado
      self.base=self.lado
      self.altura= self.lado*(3/2)**1/2

    def compute_area(self):
       return super().compute_area()

    def compute_perimeter(self):
       return self.lado*3
    
    def compute_inner_angles(self):
       return 180/3
    
class Isoceles(Triangle):
    def __init__(self, lado,base,altura):
      super().__init__()
      self.lado=self.lado
      self.base=self.base
      self.altura= self.lado**(2)- (self.base/2)**2

    def compute_area(self):
       return super().compute_area()

    def compute_perimeter(self):
       return self.lado*2 + self.base
    
    def compute_inner_angles(self):
       pass

class Escaleno(Triangle):
    def __init__(self, lado1, lado2,base):
      super().__init__()
      self.lado1=self.lado1
      self.lado2=self.lado2
      self.base=self.base
      

    def compute_area(self):
       semiperimetro=(self.lado1 + self.lado2+ self.base)/2
       return (semiperimetro(semiperimetro-self.lado1)(semiperimetro-self.lado2)(semiperimetro-self.base))**1/2

    def compute_perimeter(self):
       return self.lado1 + self.lado2+ self.base
    
    def compute_inner_angles(self):
       pass
class TriRectangle(Triangle):
    def __init__(self, cateto_ady, cateto_op,hipotenusa,altura):
      super().__init__()
      self.cateto_ady=self.cateto_ady
      self.cateto_op=self.cateto_op
      self.hipoteusa=self.hipoteusa
      self.altura= (self.cateto_op*self.cateto_ady)/self.hipoteusa

    def compute_area(self):
       return super().compute_area()

    def compute_perimeter(self):
       return self.cateto_ady + self.cateto_op+ self.hipoteusa
    
    def compute_inner_angles(self):
       pass
```

#### Individual modules that import Shape in inheritates from it.
```python
from Shape.shape import Shape

class Rectangle(Shape):
    def __init__(self, ancho:float, alto:float):
        super().__init__()
        self.ancho=ancho
        self.alto= alto
    
    def compute_area(self):
        return self.ancho* self.alto
    
    def compute_perimeter(self):
        return 2*self.alto+ 2*self.ancho
    
    def compute_inner_angles(self):
       return 360/4

from Shape.shape import Shape
from Shape.rectangle import Rectangle

class Square(Rectangle):
    def __init__(self, lado:float):
        super().__init__()
        self.lado=lado
    
    def compute_area(self)-> float:
        return self.lado**2
    
    def compute_perimeter(self)-> float:
        return 4* self.lado
    
    def compute_inner_angles(self):
       return super().compute_inner_angles()
       
from Shape.shape import Shape

class Triangle(Shape):
    def __init__(self, base:float, altura:float):
      super().__init__()
      self.base=base
      self.altura=altura
    
    def compute_area(self):
       return self.base*self.altura/2

    def compute_perimeter(self):
       pass

    def compute_inner_angles(self):
       pass
```
