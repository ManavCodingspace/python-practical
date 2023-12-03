# python-practical

# ***Practical 1***
#**Program to find roots of a quadratic equation**
import cmath
a=int(input('Enter the value of a:'))
b=int(input('Enter the value of b:'))
c=int(input('Enter the value of c:'))

#to find a discriminant
d=(b**2)-(4*a*c)
print('The value of discriminant is:',d)

e1=(-b+cmath.sqrt(d))/(2*a)
e2=(-b-cmath.sqrt(d))/(2*a)
print(e1,e2)
