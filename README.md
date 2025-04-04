# oops

//class creation
//object creation(in static and dynamic memory)
//constructors(default,parameterised,copy)
//destructor



#include<iostream>
using namespace std;

//Creating class with keyword class
class Animal{

    private://Access specifier
    int weight;//private member cannot be accessed outside the class

    public://Access specifier
    //data_members
    int age;//4 bytes (32 bits) same is of float datatype 
    string name; // size can vary as how many characters enter , size of char is 1 byte (8 bits), for bool datatype 1 byte (8 bits) on most systems
    //member_function
    void eat(){
        cout<<"Eating"<<endl;
    }
    void sleep(){
        cout<<"Sleeping"<<endl;
    }

    int getWeight(){//fetch the weight
        return weight;
    }
    void setWeight(int weight){//set the weight
       this->weight= weight;//this->weight refers to the data member weight of the current object, distinguishing it from the parameter weight.
    }
// this is the pointer to the current object
//this is especially useful when the parameter names are the same as the data member names.


    //Constructor (also known as Default Constructor)

    Animal(){
        cout<<"Constructor is initialized"<<endl;
        //it is used to initialize the object
        this->weight=0;
        this->age=0;
        this->name="";
    }  

    //Parameterized Constructor

    Animal(int age){
        this->age=age;
        cout<<"The age of Animal is : "<<this->age<<endl;
        cout<<"Parameterized Constructor is called"<<endl;
    }
    Animal(int age,int weight){
        this->age=age;
        this->weight=weight;
        cout<<"The age of Animal is : "<<this->age<<endl;
        cout<<"The weight of Animal is : "<<this->weight<<endl;
        cout<<"Parameterized Constructor2 is called"<<endl;
    }

    //Copy Constructor

    Animal(const Animal &obj){
       this->weight=obj.weight;
       this->name=obj.name;
       this->age=obj.age; 
       cout<<"Copy Constructor is called"<<endl;
    }

    //Destructor

    ~Animal(){
       cout<<"Destructor is called"<<endl; 
    }
};

class Bird{

};
int main(){

    //cout<<sizeof(Bird)<<endl;
    //An empty class in C++ takes 1 byte to ensure each object has a unique memory address.


    //Object creation

    // in Static Memory
    // Animal dog;//Object "dog" of type Animal
    // dog.age=12;
    // dog.name="Leo";
    // cout<<"Age of dog is : "<<dog.age<<endl;
    // cout<<"Name of dog is : "<<dog.name<<endl;
    // dog.eat();
    // dog.sleep();
    // //To access the private member outside the class we use getters and setters
    // dog.setWeight(42);
    // cout<<"Weight of Leo is : "<<dog.getWeight()<<endl;

    //in Dynamic Memory
    
    // Animal* cat=new Animal;
    // cat->age=4;
    // cat->name="Mannya";
    // cout<<"Age of cat is : "<<cat->age<<endl;
    // cout<<"Name of cat is : "<<cat->name<<endl;
    // cat->eat();
    // cat->sleep();
    // cat->setWeight(14);
    // cout<<"Weight of Mannya is : "<<cat->getWeight()<<endl;



    //Constructor or Default Constructor

    // Animal a;//Constructor is initialized
    // Animal* b=new Animal();//Constructor is initialized



    //Parameterized Constructor

    //in Static memory
    // Animal a;
    // Animal(18);
    
    //in Dynamic memory
    //Animal* b=new Animal(20);
    //Animal* b=new Animal(20,79);



    //Copy constructor

    // Animal a;
    // Animal d;
    // Animal b=a;
    // Animal c(d);



    //Destructor ->frees up the memory i.e deletes the object
    // Destructor destroys the class objects created by the constructor. 


    //Destructor is called Automatically in static memory once the function gets over 

    // Animal a;
    // a.age=5;

    //Destructor has to be called manually in dynamic memory

    // Animal* b=new Animal;
    // b->age=12;
    // //manually delete , with the keyword delete
    // delete b;

    //destructor is the last function that is going to be called before an object is destroyed.
    return 0;
}




//encapsulation

#include <iostream>
using namespace std;

class Employee {


  private:

    //private attribute
    int salary;
    
  public:

    //setter
    void setSalary(int salary) {
      this->salary = salary;
    }

    //getter
    int getSalary() {
      return salary;
    }
};

int main() {
  Employee* emp=new Employee;
  emp->setSalary(50000);
  cout << emp->getSalary();
  return 0;
}



//inheritance->inherites the property from the base class and may have its own properties

#include<iostream>
using namespace std;

//Base class

class Animal{
    public:
    int age;
};


//Derived class

//public mode of inheritance for the data available with access modifier public in class Animal
// class Dog:public Animal{
////Data members and member functions of public access modifier can be accessed outside the class  
// };

//protected mode of inheritance for the data available with access modifier public in class Animal
// class Dog:protected Animal{
// it is a Derived class "Dog" from the Base class "Animal" so the protected data members and member functions of the base class can 
// be accessed by the member functions of the derived class
// public:
// void setAge(int age){
//     this->age=age;
// }
// void getAge(){
//     cout<<this->age<<endl;
// }
//};

// //private mode of inheritance for the data available with access modifier public in class Animal
// class Dog:private Animal{
// //data members and member functions of the private class can only be accessed by the member function of the same class

// public:
// void setAge(int age){
//     this->age=age;
// }
// void getAge(){
//     cout<<this->age<<endl;
// }
// };

int main(){
    
//public mode of inheritance for the data available with access modifier public in class Animal
    // Dog d1;
    // d1.age=10;
    // cout<<d1.age<<endl;

//protected mode of inheritance for the data available with access modifier public in class Animal
    // Dog d2;
    // d2.age=10;
    // cout<<d2.age<<endl;//cannot be accessed as it is protected

    // d2.setAge(12);
    // d2.getAge();

//private mode of inheritance for the data available with access modifier public in class Animal
    //Dog d3;
    // d3.age=8;
    // cout<<d3.age<<endl;//cannot be accessed as it is private
 
    // d3.setAge(8);
    // d3.getAge();

    return 0;
}


//types of inheritance

#include<iostream>
using namespace std;

//Single level inheritance

//In single inheritance, a class is allowed to inherit from only one class.
//i.e. one base class is inherited by one derived class only.

//parent class
class Car{
    public:
    string name;
    int weight;
    int age;
    void speedUp(){
        cout<<"Speeding Up"<<endl;
    }
    void applyBreaks(){
        cout<<"Speeding Down"<<endl;
    }
};

//child class
class Scorpio:public Car{//we can call it as Scorpio is a car

};


//Multi level inheritance

//a derived class is created from another derived class 
//and that derived class can be derived from a base class or any other derived class. 
//There can be any number of levels.

//grandparent class
class Fruit{
    public:
    string name;//property
};

//parent class (child of grand parent)
class Mango:public Fruit{
    public:
    int weight;//property
};

//child class
class Alphanso:public Mango{
    public:
    int sugarLevel ;//property
};


//Multiple inheritance

// a class can inherit from more than one class.
//i.e one subclass is inherited from more than one base class

//parent 1
class A{
    public:
    //int physics
    int chemistry;
    A(){
        chemistry=101;
    }
};

//parent 2
class B{
    public:
    int chemistry;
    B(){
        chemistry=410;
    }
};

//child
class C:public A,public B{
    public:
    int maths;
};


//Heirarchical Inheritance

//more than one subclass is inherited from a single base class. 
//i.e. more than one derived class is created from a single base class.

//parent 
class Scooter{
    public:
    string name;
    int weight;
    int age;
    void speedUp(){
        cout<<"Speeding Up"<<endl;
    }
    void applyBreaks(){
        cout<<"Speeding Down"<<endl;
    }
};

//child 1
class Activa:public Scooter{

};

//child 2
class Access:public Scooter{

};




int main(){

    //For single level inheritance

    // Scorpio samarthWali;
    // samarthWali.speedUp();



    //For multi level inheritance

    // Alphanso a;
    // a.name="mazza";
    // a.weight=10;
    // a.sugarLevel=140;

    // cout<<"Name : "<<a.name<<endl;
    // cout<<"Weight : "<<a.weight<<endl;
    // cout<<"Sugar_Level : "<<a.sugarLevel<<endl;



    //For multiple inheritance

    //C obj;
    //obj.physics=1;
    //obj.chemistry=2;
    //obj.maths=3;

    //cout<<"Physics : "<<obj.physics<<endl;

    //cout<<"Chemistry : "<<obj.chemistry<<endl;    //will show error due to ambiguity it the chemistry
    //so we need to use scope resolution operator (::)
    //If the same variable name exists in two base classes, we can use scope resolution operator to distinguish. 
    //cout<<"Chemistry : "<<obj.A::chemistry<<endl;//class A chya chemistry cha object call zala
    //cout<<"Maths : "<<obj.maths<<endl;




    //For heirarchical inheritance

    // Activa i;
    // Access hunter;

    // i.speedUp();
    // hunter.speedUp();

    return 0;
}



//Polymorhism->Poly means "many" and morph means "forms" . So the word Polymorphism indicates many forms

//compile-time->This type of polymorphism is achieved by
// function overloading or operator overloading.

//overloading->If we create two or more members having the same name but different in number or type of parameter, 
//it is known as C++ overloading. 


#include<iostream>
using namespace std;


//function overloading->When there are multiple functions with the same name but different parameters,
//then the functions are said to be overloaded, 
//hence this is known as Function Overloading.

//function overloading->Functions can be overloaded by changing the number of arguments 
//or/and changing the type of arguments.
class Maths{
    public:
    //no. of arguments =2
    int sum(int a,int b){
        cout<<"1 is called"<<endl;
        return a+b;
    }
    //no. of arguments=3
    int sum(int a,int b,int c){
        cout<<"2 is called"<<endl;
        return a+b+c;
    }
    //type of first argument is int and second is float
    int sum(int a,float b){
        cout<<"3 is called"<<endl;
        return a+b;
    }
    //here sum() (sum function) exists in various form
};


//operator overloading->In C++, we can alter the way operators work for objects. 
//This is known as operator overloading. 
//It is one of the best features used to redefine the operators in C++ 

// Operator that cannot be overloaded are as follows:
// Scope operator (::)
// Sizeof
// member selector(.)
// member pointer selector(*)
// ternary operator(?:)


class Param{
    public:
    int val;

    void operator+(Param& obj2){
        int value1=this->val;
        int value2=obj2.val;
        cout<<(value1-value2)<<endl;
    }
};

int main(){

    //For function overloading

    // Maths obj;
    // cout<<obj.sum(2,5)<<endl;
    // cout<<obj.sum(1,2,3)<<endl;
    // cout<<obj.sum(5,2.5f)<<endl;//explicit or mannual typecasting

    //For operator overloading

    Param obj1,obj2;
    obj1.val=7;
    obj2.val=2;

    //this should print the difference between them
    obj1+obj2;//obj1 object chya sathi "+" operator chya defination la class madhe search kela janar jithe obj2 ha i/p parameter mhanun gela asnar
    //i.e obj1.add(obj2)->"obj1" ha current object asto "add" ha function call(member function) asto ani "obj2" ha i/p parameter asto
    return 0;
}




//Polymorphism

//Run-time->

#include<iostream>
using namespace std;

class class_name{
    public:

};

int main(){

    return 0;
}
