# coffee-shop
 Coffee Shop Domain Model

This project implements an Object-Oriented Domain Model for a coffee shop, establishing and managing the relationships between three core entities: Customer, Coffee, and Order. It utilizes Python and object-oriented principles to enforce data integrity, manage associations, and provide aggregate functionality.

 Objective

The goal of this project is to model a many-to-many relationship between Customer and Coffee through a single join class, Order.

Relationship Summary:

Class

Relationship

Role

Customer

One-to-Many

Has many Orders.

Coffee

One-to-Many

Has many Orders.

Order

One-to-One

Belongs to one Customer and one Coffee.

 Setup and Installation

Follow these steps to set up the project and environment.

Prerequisites

Python 3.8+

Pipenv

Installation Steps

Clone the Repository (or navigate to your project directory):

cd coffee_shop


Set up the Virtual Environment using Pipenv:
This command creates the virtual environment and installs the necessary packages (including pytest).

pipenv install


Activate the Virtual Environment:

pipenv shell


 Project Structure

The repository is structured as follows, adhering to standard Python project organization:

coffee_shop/
├── customer.py         # Defines the Customer class and methods
├── coffee.py           # Defines the Coffee class and methods
├── order.py            # Defines the Order class (the join table) and methods
├── debug.py            # Interactive script for testing and debugging
├── Pipfile             # Project dependencies
├── Pipfile.lock        # Locked dependencies file
└── tests/
    ├── __init__.py
    ├── test_customer.py
    ├── test_coffee.py
    └── test_order.py


 Domain Model Implementation Details

Data Integrity

All classes implement properties (@property and @<attribute>.setter) to ensure data integrity and validation checks:

Class

Attribute

Constraint / Validation

Customer

name

String, length between 1 and 15 characters.

Coffee

name

String, at least 3 characters long.

Order

price

Float, between 1.0 and 10.0 (inclusive).

Order

customer

Must be an instance of Customer.

Order

coffee

Must be an instance of Coffee.

Key Methods and Functionality

Class

Method / Property

Description

Customer

orders()

Returns a list of all Order instances placed by the customer.

Customer

coffees()

Returns a unique list of Coffee instances the customer has ordered.

Customer

create_order(coffee, price)

Creates and returns a new Order instance, associating it with the customer and the provided coffee.

Customer

most_aficionado(coffee)

Class Method: Returns the Customer instance who has spent the most money on the specified Coffee.

Coffee

orders()

Returns a list of all Order instances for this coffee.

Coffee

customers()

Returns a unique list of Customer instances who have ordered this coffee.

Coffee

num_orders()

Returns the total count of orders placed for this coffee.

Coffee

average_price()

Returns the average price of orders for this coffee.

 Running Tests

All class logic, validation, and relationship methods are covered by unit tests in the tests/ directory.

Ensure you have activated your virtual environment (pipenv shell).

Run pytest from the project root:

pytest


 Interactive Debugging

To interactively test and verify the relationships and methods, run the debug.py file:

python debug.py


This file contains example object creation and method calls for hands-on verification.