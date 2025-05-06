# Pet-Adoption-System
'''
Function to implement the usage of the Pet Adoption System
'''
import random
#pet base class
class Pet:
    def __init__(self,name,species,age):
        self.name=name
        self.age=age
        self.species=species
        
# displaying the  pet information
    def display_info(self):
        print(f"Name:{self.name},Age:{self.age},species:{self.species}")

#dog class
class Dog(Pet):
    def __init__(self,name,age,breed,colour):
        super().__init__(name,"dog",age)
        self.breed=breed
        self.colour=colour

# displaying the  dog information 
    def display_info(self):
        super().display_info()
        print(f"Breed:{self.breed},Colour:{self.colour}")

#cat class
class Cat(Pet):
    def __init__(self,name,age,breed,colour):
        super().__init__(name,"cat",age)
        self.breed=breed
        self.colour=colour


# displaying the cat information
    def display_info(self):
        super().display_info()
        print(f"Breed:{self.breed},Colour:{self.colour}")

#preferences for the pets
pet_preferences={
    "dog": ("Bones","walk"),
    "cat": ("Meow","Fish")
    }

#storage of pets in the dictionary format
pets={}

# Function for adding the pets
def add_pet():
    pet_type=input("Enter the pet type(dog/cat):")
    name=input("Enter the pet name:")
    age=int(input("Enter the pet age:"))
    breed=input("Enter the pet breed:")
    colour=input("Enter the pet colour:")

    pet_id=random.randint(786,789)
    while pet_id in pets:
        pet_id=random.randint(786,789)
        if pet_type=="dog":
            pet=Dog(name,age,breed,colour)
        elif pet_type=="cat":
            pet=Cat(name,age,breed,colour)
        else:
            print("Invalid pet type")
            return
            pets[pet_id]=pet
            print(f"Pet added with ID:{pet_id}")

# Function for Adopting a pet
def adopt_pet():
    pet_id=int(input("Enter the pet ID:"))
    if pet_id in pets:
        print("Pet adopted successfully")
        pets[pet_id].display_info()
        del pets[pet_id]
    else:
        print("Invalid pet ID or Pet ID not found")


# Function for viewing a pet
def view_pet():
    pet_id=int(input("Enter the pet ID:"))
    if pet_id in pets:
        print("Pet information:")
        pets[pet_id].display_info()

#  Function for Menu
def menu():
    print("1.Add Pet")
    print("2.Adopt Pet")
    print("3.View Pet")
    print("4.Exit")
    choice=int(input("Enter your choice(1-4):"))
    return choice
    if choice==1:
        add_pet()
    elif choice==2:
        adopt_pet()
    elif choice==3:
        view_pet()
    else:
        print("Invalid choice")
menu()
