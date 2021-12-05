""" Samantha Walsh
# 9/10/2021
# The Oregon Trail

# Description:
#   This program is a recreation of The Oregon Trail game developed by
#   Bill Heinemann, Don Rawitsch, and Paul Dillenberger

# Sources:
# 1  (Oregon Trail Info)https://en.wikipedia.org/wiki/The_Oregon_Trail_(series)
# 2  (Oregon Trail Game)https://classicreload.com/oregon-trail.html
# 3  (If statements)https://www.w3schools.com/python/python_conditions.asp
# 4  (Booleans)https://www.w3schools.com/python/python_booleans.asp
# 5  (Functions)https://www.w3schools.com/python/python_functions.asp
# 6  (Time module)https://www.programiz.com/python-programming/time
# 7  (Operators)https://www.w3schools.com/python/python_operators.asp
# 8  (While loops)https://www.w3schools.com/python/python_while_loops.asp
# 9  (While loops)https://wiki.python.org/moin/WhileLoop
# 10 (Exceptions)https://www.w3schools.com/python/python_ref_exceptions.asp
# 11 (Lists)https://www.w3schools.com/python/python_lists_comprehension.asp
# 12 (Date/Time Module)https://www.w3schools.com/python/python_datetime.asp
# 13 (Date)https://www.guru99.com/date-time-and-datetime-classes-in-python.html
# 14 (String Formatting)https://realpython.com/python-string-formatting/
# 15 (Try/Except)https://www.w3schools.com/python/python_try_except.asp
# 16 (.upper)https://www.w3schools.com/python/ref_string_upper.asp
# 17 Andrew Krupp (Student Assistant)
# 18 Prof. Scott Vanselow


# I will refer to these sources by number throughout the program
# I removed all global variables by Prof. Vanselow's recommendation.

###############################################################################
"""
__author__ = "Samantha Walsh"

# Importing the time and datetime modules (Source 6)
import time
import datetime
from threading import Timer
import random


# Defining functions (Source 5)
def main():
    """ The main() function contains the entirety of the game.
    """
    # INTRODUCTION
    print("Hello! My name is Sam!")
    time.sleep(2)  # Time Module (Source #6)
    print("This is my recreation of the Original Oregon Trail game.")
    print("I hope you enjoy playing! :)")
    time.sleep(2)
    print("-" * 150)  # Using the * String operator
    # Instead of typing "-" 150 times, I told Python to multiply
    # the string "-" by 150.
    time.sleep(2)

    # GAME CHOICES
    print("\nWelcome to the Oregon Trail!")
    time.sleep(2)
    print("""\nMany kinds of people made the trip to Oregon.
    \tYou may:
    \t\t1. Be a banker from Boston
    \t\t2. Be a carpenter from Ohio
    \t\t3. Be a farmer from Illinois
    \t\t4. Find out the differences between these choices\n""")

    # The user will first decide their career
    # The user's career choice will affect their funds, supplies,
    # and ability to survive (later on)

    # I am calling to the functions by assigning the function to a variable.
    # The value returned by the function will be assigned to the variable.
    # These functions will allow the user to decide their career and will
    # determine the amount of money the user will get based on their choice.
    # A function will also allow the user to choose a different career.
    # Then the user will decide the names of the people in their party.
    main_career = career_choice()
    main_funds = career_choice_funds(main_career)
    check_career_choice(main_career)
    print("You will be the wagon leader.")
    time.sleep(2)
    print("You will be traveling your spouse and three kids.")
    time.sleep(2)
    print("-" * 150)
    family_names_list = family_names()  # Will use later
    check_family_names()

    # START GAME
    # The user will decide which month to leave. Later on, this month
    # choice will affect their survival.
    print("""
It is 1848. Your jumping off place for Oregon is Independence, Missouri.
You must decide which month to leave Independence.
    """)
    time.sleep(2)
    print("\t1. March", "2. April", "3. May", "4. June", "5. July",
          "6. Ask for advice\n", sep="\n\t")  # Using sep
    time.sleep(1)
    main_month = month_choice()  # Calling to month_choice() using a variable

    # GENERAL STORE INTRO
    print("Before leaving Independence you should buy equipment and "
          "supplies.")
    time.sleep(2)
    print("You have $%.2f in cash but you don't have to spend it all now."
          % main_funds)
    # Formatting strings (Source 13)
    time.sleep(2)
    print("You can buy whatever you need at Lou's general store.")
    time.sleep(2)
    print("\nLet's head there now.\n")
    time.sleep(2)
    print("-" * 150)
    time.sleep(2)

    # LOU'S GENERAL STORE DIALOGUE
    print("\n'Howdy there partner! The names' Louis but you can call me Lou.'")
    time.sleep(2)
    print("'So yer' going to Oregon! Them trails is dangerous...'")
    time.sleep(2)
    print("'Lucky for you, we got everything y'all will need.'")
    time.sleep(2)
    print("'Here's what I recommend for new comers...'")
    time.sleep(2)
    print("(Lou hands you a wrinkled piece of paper.)")
    time.sleep(2)
    print("(The handwriting looks like a child's and it's filled with "
          "spelling mistakes.)")
    time.sleep(2)
    print("(You can just barely make out what it says...)")
    time.sleep(2)
    print("""
\t~ a team of oxen to pull your wagon
\t~ clothing for summer and winter
\t~ plenty of food
\t~ ammunition for your rifles
\t~ spare parts for your wagon\n""")
    time.sleep(3)
    print("-" * 150)
    time.sleep(1)

    # Now I am assigning variables for my general_store() and
    # general_store_calculator() functions.

    main_pay_items = "pay"
    main_exit_store = "exit"

    # Calling to functions with multiple arguments

    main_inventory = inventory(general_store_calculator(main_month, main_funds,
                                                        main_pay_items,
                                                        main_exit_store))

    print("-" * 100)
    print()
    time.sleep(2)
    print("Now you will start your journey to Oregon...")
    time.sleep(2)
    print("Each round of choices counts for 2 weeks of travel time.")
    time.sleep(2)
    print("If you survive 12 rounds (6 months of travel) you win the game.")
    time.sleep(2)
    print("Each round you will be able to hunt for food, "
          "trade with travellers, and ration your food.")
    time.sleep(2)
    print("Watch out for bandits and snakes. Good luck...")
    time.sleep(2)

    main_miles = 0
    current_date = datetime.datetime(1848, main_month + 2, 1)
    two_weeks = datetime.timedelta(weeks=2)  # Source 18
    main_weather = current_weather(current_date)

    # MAIN GAME 12 ROUNDS OF PLAY
    # This is the main loop that will allow the user to make choices for each
    # round of play.
    for rounds in range(12):
        empty_list = []
        lost_the_game = False
        while not lost_the_game:
            if family_names_list == empty_list:
                print("Everyone has died. You have lost the game.")
                lost_the_game = True
                break
            elif main_inventory[0] <= 0:
                print("You have no more money. You have lost the game.")
                lost_the_game = True
                break
            elif main_inventory[1] <= 0:
                print("You have no more oxen. You have lost the game.")
                lost_the_game = True
                break
            elif main_inventory[2] <= 0:
                print("You have no more food. You have lost the game.")
                lost_the_game = True
                break
            else:
                continue
        trail_day_info(current_date, main_miles, main_inventory, main_weather)
        user_making_choice = True
        while user_making_choice:  # user decides if they want to hunt
            try:
                local_hunt = int(input("Do you want to hunt (1) or "
                                       "continue (2)? "))
                if local_hunt == 1:
                    main_inventory = hunting(main_inventory)
                    user_making_choice = False
                elif local_hunt == 2:
                    print("Ok. Let's continue.")
                    time.sleep(2)
                    user_making_choice = False
                else:
                    print("I'm sorry, I didn't understand that. "
                          "Please type 1 or 2. ")
            except ValueError:
                print("I'm sorry, I didn't understand that. "
                      "Please type 1 or 2. ")
        main_inventory = rations(main_inventory)
        main_inventory = random_event(family_names_list, main_inventory)
        family_names_list, main_inventory = random_event(family_names_list,
                                                         main_inventory)
        if rounds == 4 or rounds == 8 or rounds == 12:
            main_inventory = inventory(
                general_store_calculator(main_month, main_funds,
                                         main_pay_items,
                                         main_exit_store))
        main_miles += 150
        current_date += two_weeks
    if lost_the_game:
        exit()
    else:
        print("Congrats! You have won the game!")


# CAREER CHOICE FUNCTION
def career_choice():
    """Function that allows the user to decide their career.

The career choice function allows the user to decide their career.
This function takes a user input of 1,2,3, or 4. It outputs the user's
career choice for later use in other functions. If the user picks choice 4,
the user will receive a description of the choices.

I had originally had the career_choice() function include the code within
the career_choice_funds() and career_choice_points() functions however
Andrew Krupp (Student Assistant) recommended I return only one value
per function (or do only one thing) instead of three so that it would be
less confusing.

Returns:
    career: user's career choice as an int
"""
    career_info = 4
    user_making_choice = True  # Booleans (Source 4)
    # When user_making_choice is False, the loop will break
    while user_making_choice:  # While loops (Sources 8 and 9)
        try:  # try/except statements (Source 15)
            career = int(input("What is your choice? Type 1,2,3, or 4. "))
            if career == career_info:  # Using == operator (Source 7)
                print("""
\tTraveling to Oregon isn't easy! But if you're a banker, you'll have 
\tmore money for supplies and services than a carpenter or a farmer.

\tHowever, the harder you have to try, the more points you deserve!
\tTherefore, the farmer earns the greatest number of points and the
\tbanker earns the least.\n""")
            # This is the same as saying 0 < career < 6
            elif not career > 0 and not career < 6:  # Using 'and' and 'not'
                print("Sorry, I didn't understand that. Please type 1,2,3, "
                      "or 4. ")
            else:
                user_making_choice = False
                # Break in loop
        except ValueError:  # Built in exception (Source 10)
            print("Sorry, I didn't understand that. Please type 1,2,3, or 4. ")
    return career
    # Return (Source 5)


# CAREER FUNDS
def career_choice_funds(career):
    """Function that determines the user's funds based on their career choice.

The career_choice_funds function will take in the parameter of the
user's career choice from career_choice() and output the amount of money
they will get based on that choice.

Parameter:
    career(int): user's career choice from the career_choice() function

Returns:
    local_funds(float): the amount of funds the user will have based on their
    career choice
"""
    banker = 1
    carpenter = 2
    farmer = 3
    local_career = career
    if local_career == banker:
        local_funds = 1600.00
    elif local_career == carpenter:
        local_funds = 800.00
    elif local_career == farmer:
        local_funds = 400.00
    return local_funds


# For checking if user's input is correct/incorrect in multiple functions
correct = "Y"
incorrect = "N"


# CHECK CAREER CHOICE FUNCTION
def check_career_choice(career):
    """Checks if the user would like to change their career choice.

This functions checks if user's career choice was what they wanted and
allows the user to change their career choice.

Parameters:
    career(int): user's career choice from the career_choice() function
    """
    user_making_choice = True
    while user_making_choice:
        try:
            correct_career = str(
                input("You chose career number " + str(career) +
                      ". Is that correct? Type Y or N. "))
            # String Concatenation
            if correct_career.upper() == correct:  # Using .upper() (Source 16)
                print("Great! Next, you will choose the names for the members "
                      "of your party.")
                time.sleep(2)
                user_making_choice = False
            elif correct_career.upper() == incorrect:
                print("Which career would you like instead? ")
                career_choice()
            else:
                print("Sorry, I didn't understand that. Please type Y or N.")
        except ValueError:
            print("Sorry, I didn't understand that. Please type Y or N.")


# PRINT FAMILY NAMES FUNCTION
def family_names():
    """Allows user to input family names and function outputs family names.

This function allows the user to input their name and the names of their
party members. The function then prints out all the family names.
I use this function in the check_family_names() functions so that if the
user decides to change a name, it will output the new names.
This function returns a list containing the string names of the party.
Later I will user this list to randomize death, injury, and sickness.

Returns:
    A list of strings containing the user's family name choices.
    """
    wagon_leader = str(input("What is the name of the wagon leader? "))
    spouse = str(input("What is your spouse's name? "))
    oldest_child = str(input("What is the name of your eldest child? "))
    middle_child = str(input("What is the name of your middle child? "))
    youngest_child = str(input("What is the name of your youngest child? "))
    print("\nOk. Here is your party: ")
    print(" 1. " + wagon_leader)  # String operator +
    print(" 2. " + spouse)
    print(" 3. " + oldest_child)
    print(" 4. " + middle_child)
    print(" 5. " + youngest_child)
    return [wagon_leader, spouse, oldest_child, middle_child, youngest_child]


# CHECK FAMILY NAMES
def check_family_names():
    """Checks if the user would like to change their family names.

The check_family_names() function asks the user whether or not the names
they entered in the family_names() function is correct.
    """
    user_making_choice = True
    while user_making_choice:
        correct_names = str(input("\nAre these names correct? Type Y or N. "))
        if correct_names.upper() == incorrect:
            print("Ok. Please re-enter your party's names\n")
            time.sleep(1)
            family_names()
        elif correct_names.upper() == correct:
            print("\nGreat! We are ready to start.")
            print("-" * 150)
            time.sleep(2)
            user_making_choice = False
        else:
            print("I'm sorry, I didn't understand that. Please type Y or N.")


# Variables used in the month_choice() function
month_name = ["March", "April", "May", "June", "July"]
month_info = 6


# MONTH CHOICE FUNCTION
def month_choice():
    """Allows the user to choose which month they will leave for Oregon.

This function will ask the user which month of the year they want to leave.
Their month choice will affect survival of the weather. The function returns
the month choice which will be used in other functions to display the date
determine the weather.

Returns:
    local_month(int): user's month choice as an integer
    """
    user_making_choice = True
    while user_making_choice:
        try:
            local_month = int(
                input("Which month would you like to leave? Please"
                      " type 1,2,3,4,5, or 6. "))
            if 0 < local_month < 6:
                print("\nOk. You will be leaving for Oregon in " +
                      month_name[local_month - 1] + ".")
                time.sleep(2)
                user_making_choice = False
            elif local_month == month_info:
                print("""
You attend a public meeting held for "folks with the California-Oregon fever."
You're told:
\t"If you leave too early, there won't be any grass for your oxen to eat.
\tIf you leave too late, you may not get to Oregon before winter comes.
\tIf you leave at just the right time, there will be green grass
\tand the weather will still be cool."\n""")
            else:
                print("Sorry, I didn't understand that. "
                      "Please type 1,2,3,4,5, or 6. ")
        except ValueError:  # Built in exception (Source 11)
            print("Sorry, I didn't understand that. "
                  "Please type 1,2,3,4,5, or 6. ")
    return local_month


# GENERAL STORE
def general_store(local_month, local_funds, local_oxen, local_food,
                  local_clothing, local_ammunition, local_spare_parts,
                  local_total_amount):
    """Displays the user's item choices and how much they will spend.

This function will display the date, their item options, how much they've
spent (Will start at 00.00), and how much money they have. This function
is used in the general_store_calculator function so that after each
item is selected and purchased, the general_store() function will display
the new amount.

Parameters:
    local_month(int): user's choice from month_choice() function
    local_funds(float): user's funds from career_choice_funds()
    local_oxen(int): amount spent on oxen
    local_food(float): amount spent on food
    local_clothing(int): amount spent on clothing
    local_ammunition(int): amount spent on ammunition
    local_spare_parts(int): amount spent on spare parts
    local_total_amount(float): total amount spent
    :rtype: object
    """
    date = datetime.datetime(1848, local_month + 2, 1)
    print("-" * 150)
    print("\nLou's General Store \nIndependence, Missouri")
    print(date.strftime("%B %d, %Y\n"))  # Date/Time (Source 14)
    print("Items Available:         Amount spent per item:")
    print(" 1. Oxen                 $" + format(local_oxen, '.2f'))
    print(" 2. Food                 $" + format(local_food, '.2f'))
    print(" 3. Clothing             $" + format(local_clothing, '.2f'))
    print(" 4. Ammunition           $" + format(local_ammunition, '.2f'))
    print(" 5. Spare Parts          $" + format(local_spare_parts, '.2f')
          )
    print("-" * 50)
    print("Amount you have:         $" + format(local_funds, '.2f'))
    print("Total cost:              $" + format(local_total_amount, '.2f'))
    print('\nType "Pay" to Pay for Items')  # Pay for items
    print('Type "Exit" to exit the store\n')  # Leave Store
    print("-" * 150)


# GENERAL STORE CALCULATOR
def general_store_calculator(local_month, local_funds, pay_items, exit_store):
    """Allows user to choose item to purchase and calculates amount.

This function will ask the user how many items they want and calculate the
amount the user owes. The function will also tell the user if they don't have
enough money and will kick them out of the store if they don't have enough.
I have to use many parameters for this function because I am using variables
from the main() function.

Parameters:
    local_month(int): user's choice from month_choice() function
    local_funds(float): user's funds from career_choice_funds()
    pay_items(str): contains "pay", if user types pay, funds will change
    exit_store(str): contains "exit, it user types exit, user will exit store
    """
    oxen = 1
    food = 2
    clothing = 3
    ammunition = 4
    spare_parts = 5
    local_oxen = 0.00
    local_food = 0.00
    local_clothing = 0.00
    local_ammunition = 0.00
    local_spare_parts = 0.00
    local_total_amount = 0.00
    user_making_choice = True
    while user_making_choice:
        general_store(local_month, local_funds, local_oxen, local_food,
                      local_clothing, local_ammunition, local_spare_parts,
                      local_total_amount)
        item_choice = input("Which item would you like to purchase? Please "
                            "type 1,2,3,4, or 5. ")
        if str(item_choice.lower()) in pay_items:
            # If the user has enough money, they will pay.
            if (local_funds - local_total_amount) >= 0.00:
                print("Your total is $" +
                      format((local_oxen + local_food + local_clothing +
                              local_ammunition + local_spare_parts), '.2f'))
                time.sleep(2)
                print("You now have $" + format((local_funds -
                                                 local_total_amount), '.2f') +
                      " left.")
                time.sleep(2)
                local_funds -= local_total_amount
                print("You have exited the store.")
                user_making_choice = False
            # If the user does not have enough money, they will be kicked out.
            elif (local_funds - local_total_amount) < 0.00:
                print("'What in tarnation?! You haven't got a penny "
                      "to your name. Get out of my store 'for I "
                      "call the police.'")
                time.sleep(2)
                print("You have exited the store.")
                user_making_choice = False
                time.sleep(1)
        elif str(item_choice) in exit_store:
            # If the user does not want to purchase anything they can exit.
            print("You have exited the store.")
            user_making_choice = False
            time.sleep(2)
        elif int(item_choice) == oxen:
            # If the user picked oxen (1) they will be asked how many they want
            print("\n\t'There are 2 oxen in a yoke. "
                  "I recommend at least 3 yoke.'")
            print("\t'I charge $40 a yoke.'\n")
            number_of_items = int(input("\t'How many yoke do you want?' "))
            print("\t" + str(number_of_items) + " yoke is " +
                  str(number_of_items * 2) + " oxen.")
            time.sleep(2)
            print("\tThat will cost: $" + format((number_of_items * 40.00),
                                                 '.2f'))
            time.sleep(2)
            # Calculating the cost based on the number of items the user wants
            local_oxen += (number_of_items * 40.00)
            local_total_amount += (number_of_items * 40.00)
            time.sleep(1)
        elif int(item_choice) == food:
            # If the user picked food (2) they can pick how much they want.
            print("""\n\t'I recommend you take at least 200 pounds of 
\tfood for each person in your family. I see that you have 
\t5 people in all. You'll need flour, sugar, bacon, and coffee. 
\tMy price is 20 cents a pound.'\n""")
            number_of_items = int(input("\t'How many pounds of food "
                                        "do you want? "))
            print("\t" + str(number_of_items) + " pounds of food will give "
                                                "each person " + str(
                number_of_items / 5) + " pounds of "
                                       "food to eat.")
            time.sleep(2)
            # Then it will calculate the cost and how many pounds of food
            # each person will get.
            print("\tThat will cost: $" + format((number_of_items * 0.20),
                                                 '.2f'))
            local_food += (number_of_items * 0.20)
            local_total_amount += (number_of_items * 0.20)
            time.sleep(1)
        elif int(item_choice) == clothing:
            # If the user picked clothing (3)
            print("""\n\t'You'll need warm clothing in the mountains. 
\tI recommend taking at least 2 sets of clothing per person. 
\tEach set is $10.'\n""")
            number_of_items = int(input("\t'How many sets of clothes "
                                        "do you want? "))
            print("\tOk. You will have " + (str(number_of_items // 5)) +
                  " sets of clothing per person.")
            time.sleep(2)
            # It will display how many sets of clothing each family
            # member will have.
            if (number_of_items % 2) == 0:
                print("\tEach person will have the same number of "
                      "clothing sets.")
            elif (number_of_items % 2) != 0:
                print("\tUh oh! Someone will not have the same number of "
                      "clothes as everyone else.")
            time.sleep(2)
            # Using the modulus % operator to determine if each family member
            # has the same number of clothes.
            print("\tThat will cost: $" + format((number_of_items * 10), '.2f'
                                                 ))
            local_clothing += (number_of_items * 10)
            local_total_amount += (number_of_items * 10)
            time.sleep(1)
        elif int(item_choice) == ammunition:
            # If the user picked ammunition (4)
            print("\n\t'I sell ammunition in boxes of 20 bullets. "
                  "Each box costs $2'")
            number_of_items = int(input("\t'How many boxes of bullets "
                                        "do you want?' "))
            print("\tOk. That will cost: $" + format((number_of_items * 2),
                                                     '.2f'))
            local_ammunition += (number_of_items * 2)
            local_total_amount += (number_of_items * 2)
            time.sleep(1)
        elif int(item_choice) == spare_parts:
            # If the user picked spare parts (5)
            print("""\n\t'It's a good idea to have a few spare parts 
\tfor your wagon. Spare parts cost $10 each.'""")
            number_of_items = int(input("\t'How many spare parts do you want?"
                                        "' "))
            print("\tOk. That will cost: $" + format((number_of_items * 10),
                                                     '.2f'))
            local_spare_parts += (number_of_items * 10)
            local_total_amount += (number_of_items * 10)
            time.sleep(1)
        elif int(item_choice) < 1 or int(item_choice) > 5:
            print("Sorry, I didn't understand that. Please "
                  "type 1,2,3,4,5, Pay, or Exit.")
            # If the user did not type 1,2,3,4,5 pay, or exit.
            time.sleep(1)
    return [local_funds, local_oxen, local_food, local_clothing,
            local_ammunition, local_spare_parts]


# INVENTORY
def inventory(general_store_list):
    """Will create a list containing the user's inventory items.

The inventory() function uses the amount spent in the
general_store_calculator() function to keep track of the amount of items in
in the user's inventory. This is calculated based off the cost
of each of the items. I used floor division so that it is rounded to
a whole number.

Returns:
    A list containing the user's inventory items as floats and integers
    """
    funds = 0
    oxen = 1
    food = 2
    clothing = 3
    ammunition = 4
    spare_parts = 5
    inventory_items = [float(general_store_list[funds]),
                       int(((general_store_list[oxen]) // 40) * 2),
                       float((general_store_list[food]) // 0.20),
                       int((general_store_list[clothing]) // 10),
                       int((general_store_list[ammunition]) // 2),
                       int((general_store_list[spare_parts]) // 10)]
    return inventory_items


# HUNTING
def hunting(local_inventory):
    """Allows the user to hunt for food.

The hunting() function gives the user a time limit to type BANG
If the user types BANG correctly within the time limit, they
will get a random amount of food between 50 and 200 pounds. The user
only gets three tries at hunting total. Every time a shot is fired
5 boxes of bullets are used. This is because one "day" in the oregon trail
is actually worth two weeks.

Parameters:
    local_inventory: list of inventory item amounts from inventory()
    """
    food = 2
    ammunition = 4
    for tries in range(3):
        timeout = 2
        t = Timer(timeout, print, ["Sorry, you weren't quick enough!"])
        t.start()
        hunt_bang = input("QUICK! Type BANG: ")
        t.cancel()
        if hunt_bang == "BANG":
            print("\nRight between the eyes! You got a big one!")
            local_meat = random.randint(50, 200)
            print("You got " + str(local_meat) + " pounds of meat!")
            local_inventory[ammunition] -= 5
            local_inventory[food] += local_meat
            time.sleep(1)
        else:
            print("Better luck next time!")
            choice = input("Would you like to try again? Type y or n. ")
            if choice.upper() == correct:
                continue
            elif choice.upper() == incorrect:
                break
    print("\nI think that's enough hunting for today.")
    return local_inventory


# RATIONS
def rations(local_inventory):
    """Allows the user to choose how much to ration their food for the week.

The rations function allows the user to determine how they will ration
their food for the next two weeks. Poor is 1 pound of food per person, per
day. Moderate is 2 pounds of food per person, per day. Well is 3 pounds of
food per person, per day.

Parameters:
    local_inventory: list of inventory item amounts from inventory()
    """
    food = 2
    family = 5
    poorly = 1
    moderately = 2
    well = 3
    user_making_choice = True
    print("How do you want to ration your food?")
    print("""Do you want to eat: 
\t1. Poorly
\t2. Moderately
\t3. Well""")
    while user_making_choice:
        try:
            local_rations = int(input("What is your choice? "))
            if local_rations == poorly:
                print("You and your family will eat poorly for the next two "
                      "weeks. This may impact your health. ")
                if (local_inventory[food] - ((poorly * family) * 14)) < 0:
                    print("I'm sorry, you do not have enough food for that. "
                          "You need to go hunting.")
                    hunting(local_inventory)
                elif (local_inventory[food] - ((1 * family) * 14)) >= 0:
                    local_inventory[food] -= ((1 * family) * 14)
                    user_making_choice = False
            elif local_rations == moderately:
                print("You and your family will eat moderately for the next "
                      "two weeks. Your family is ok with this.")
                if (local_inventory[food] - ((moderately * family) * 14)) < 0:
                    print("I'm sorry, you do not have enough food for that. ")
                elif (local_inventory[food] - ((2 * family) * 14)) >= 0:
                    local_inventory[food] -= ((2 * family) * 14)
                    user_making_choice = False
            elif local_rations == well:
                print("You and your family will eat moderately for the next"
                      "two weeks. You're family seems happy about this.")
                if (local_inventory[food] - ((well * family) * 14)) < 0:
                    print("I'm sorry, you do not have enough food for that. ")
                elif (local_inventory[food] - ((3 * family) * 14)) >= 0:
                    local_inventory[food] -= ((3 * family) * 14)
                    user_making_choice = False
            else:
                print("I'm sorry, I didn't understand that. Please type 1,"
                      "2, or 3.")
        except ValueError:
            print("I'm sorry, I didn't understand that. Please type 1,"
                  "2, or 3.")
    return local_inventory


# WEATHER
def current_weather(current_date):
    """Determines weather based on current date.

Parameters:
    current_date: from main(), changed in for loop
    :return:
    """
    if current_date.month == 1 or current_date.month == 12:
        weather = "frigid"
    elif current_date.month == 2 or current_date.month == 11:
        weather = "cold"
    elif current_date.month == 3 or current_date.month == 9 or \
            current_date.month == 10:
        weather = "cool"
    elif current_date.month == 4:
        weather = "rainy"
    elif current_date.month == 5 or current_date.month == 8:
        weather = "warm"
    elif current_date.month == 6 or current_date.month == 7:
        weather = "hot"
    return weather


# SICKNESS CHOICES
def sickness_choices(event_family_names, random_family, event_inventory):
    """Allows the user the choice of how to treat sickness.

The user can either pay $50 to see a doctor, try and find a plant to cure
the sickness (33% of the time results in death) or do nothing and hope it
gets better(50% of the time results in death).

Parameters:
    event_family_names(list): family names list from initial character creation
    random_family(int): randomizes the death of a family member
    event_inventory(list): inventory from inventory function

Returns:
    event_family_names: updated family names list
    event_inventory: updated inventory
    """
    funds = 0
    user_making_choice = True
    while user_making_choice:
        doctor = 1
        plant = 2
        nothing = 3
        try:
            user_choice = int(input("What is your choice? "))
            if user_choice == doctor:
                if event_inventory[funds] > 50:
                    print(event_family_names[random_family] +
                          "saw a local doctor and was given medicine.")
                    print(
                        "Your funds are now " + format((event_inventory[funds]
                                                        - 50), '.2f'))
                    event_inventory[funds] -= 50
                    user_making_choice = False
                else:
                    print("I'm sorry you don't have enough money for that. "
                          "Please pick option 2 or 3.")
            elif user_choice == plant:
                print("You go out and search for a plant to cure " +
                      event_family_names[random_family] + ".")
                print("You find three plants. One spiky, one smooth, and one "
                      "bumpy.")
                event_family_names = plant_death(event_family_names,
                                                 random_family)
                user_making_choice = False
            elif user_choice == nothing:
                print("You choose to do nothing. " +
                      event_family_names[random_family] +
                      " may or may not get better.")
                time.sleep(2)
                random_do_nothing = random.randint(1, 2)
                if random_do_nothing == 1:
                    print("It's been a few days. It looks like " +
                          event_family_names[random_family] +
                          " is feeling better.")
                    user_making_choice = False
                elif random_do_nothing == 2:
                    print("It's been a few days. It looks like "
                          + event_family_names[random_family] +
                          "'s condition got worse.")
                    time.sleep(2)
                    print(event_family_names[random_family] + " has died.")
                    del event_family_names[random_family]
                    time.sleep(2)
                    user_making_choice = False
        except ValueError:
            print("I'm sorry, I didn't understand that. "
                  "Please type 1, 2, or 3.")
    return event_family_names, event_inventory


# RANDOM EVENTS
def random_event(event_family_names, event_inventory):
    """Randomizes sickness, animal attacks, and bandit attacks.

From 11 random events (6 bad and 5 good), the user will make choices based
on those random events.

Parameters:
    event_family_names(list): family names list from initial character creation
    event_inventory(list): inventory from inventory function

Returns:
    event_family_names(list): updated family names list after random event
    event_inventory(list): updated inventory after random event
    """
    random_event_int = random.randint(1, 11)
    random_family = random.randint(0, len(event_family_names))
    funds = 0
    oxen = 1
    ammunition = 4
    spare_parts = 5
    cold = 1
    found_money = 2
    bandit = 3
    good_health = 4
    dead_oxen = 5
    found_ammunition = 6
    snake_bite = 7
    found_spare_parts = 8
    broken_wheel = 9
    found_accordion = 10
    dysentery = 11
    if random_event_int == cold:
        print("Your family member " +
              event_family_names[random_family] + " has caught a cold. You "
                                                  "can either pay $50 to see "
                                                  "a doctor(1) search for a "
                                                  "plant to cure the sickness "
                                                  "(2) or do nothing and hope "
                                                  "it gets better (3).")
        time.sleep(2)
        event_family_names, event_inventory = \
            sickness_choices(event_family_names, random_family,
                             event_inventory)
    elif random_event_int == found_money:
        random_money = random.randint(1, 100)
        print("It's your lucky day! You found $" + format(random_money, '.2f')
              + ".")
        time.sleep(2)
        event_inventory[funds] += random_money
    elif random_event_int == bandit:
        random_rob = random.randint(1, (event_inventory[funds]))
        print("Uh oh! Bandits!")
        time.sleep(1)
        print("They hold you at gunpoint and steal $"
              + format(random_rob, '.2f') + ".")
        time.sleep(2)
        event_inventory[funds] -= random_rob
    elif random_event_int == good_health:
        print("Lucky you! All your family is in good health.")
        time.sleep(2)
    elif random_event_int == dead_oxen:
        random_oxen = random.randint(1, (event_inventory[oxen]))
        print("Oh no, your oxen looks sick. " + str(random_oxen)
              + "oxen died.")
        event_inventory[oxen] -= random_oxen
        time.sleep(2)
    elif random_event_int == found_ammunition:
        random_ammunition = random.randint(1, 25)
        print("Lucky you! You found {0} boxes of ammunition.".format(
            str(random_ammunition)))
        event_inventory[ammunition] += random_ammunition
    elif random_event_int == snake_bite:
        print("Your family member " +
              event_family_names[random_family] + "has been bitten by a "
                                                  "snake. You can either pay "
                                                  "$50 to see a doctor(1) "
                                                  "search for a plant to cure "
                                                  "the snake bite (2) or do "
                                                  "nothing and hope "
                                                  "it gets better (3).")
        time.sleep(2)
        event_family_names, event_inventory = \
            sickness_choices(event_family_names, random_family,
                             event_inventory)
    elif random_event_int == found_spare_parts:
        random_spare_parts = random.randint(1, 5)
        print("Lucky you! You found " + str(random_spare_parts)
              + " spare parts.")
        event_inventory[spare_parts] += random_spare_parts
    elif random_event_int == broken_wheel:
        random_broken_wheel = random.randint(1, 5)
        print("Uh oh. One of your wheels broke off. You use "
              + str(random_broken_wheel) + " spare parts to fix it.")
        event_inventory[spare_parts] += random_broken_wheel
    elif random_event_int == found_accordion:
        print("Congrats! You found an accordion! Now you can annoy your "
              "family members.")
        time.sleep(2)
    elif random_event_int == dysentery:
        print(event_family_names[random_family] + " has died of dysentery.")
        del event_family_names[random_family]
    return event_family_names, event_inventory


def plant_death(family_members, random_family):
    """Allows user to choose which plant to cure family member.

Parameters:
    family_members(list): list of family members names
    random_family(int): which family member will experience sickness

Returns:
    family_members(list): updated list if family member dies.
    """
    user_making_choice = True
    while user_making_choice:
        try:
            random_plant = random.randint(1, 3)
            plant_choice = int(input("Which plant do you choose? Spiky (1), "
                                     "smooth(2), or bumpy (3)?"))
            if 0 < plant_choice < 4:
                if plant_choice == random_plant:
                    print("You make a tea out of the plant.")
                    time.sleep(2)
                    print("You were very lucky, it cured the sickness.")
                    user_making_choice = False
                elif plant_choice != random_plant:
                    print("You make a tea out of the plant.")
                    time.sleep(2)
                    print("You were very unlucky. Unfortunately, the plant "
                          "was poisonous.")
                    time.sleep(2)
                    print(family_members[random_family] + "has died.")
                    print("You hold a funeral for " +
                          family_members[random_family] + ". Your family's "
                                                          "morale has "
                                                          "lowered.")
                    del family_members[random_family]
                    user_making_choice = False
            else:
                print("I'm sorry, I didn't understand that. "
                      "Please type 1, 2, or 3.")
        except ValueError:
            print("I'm sorry, I didn't understand that. "
                  "Please type 1, 2, or 3.")
    return family_members


# TRAIL INFO

def trail_day_info(local_date, local_miles, local_inventory, local_weather):
    """Shows the user the info for the current round.

It will print the date, the weather, the miles travelled,
and the amount of items in their inventory.

Parameters:
    local_date: current date in the game from main()
    local_miles(int): miles from main()
    local_inventory(list): inventory from inventory()
    local_weather(str): weather from current_weather() function
    """
    print(local_date.strftime("%B %d, %Y\n"))
    print("-" * 50)
    print("Weather: " + local_weather)
    print("Total miles travelled: " + str(local_miles))
    print("Funds: " + format((local_inventory[0]), '.2f'))
    print("Oxen: {0} Food: {1} Clothing: {2} Ammunition: {3} Spare Parts: {4}"
          .format(str(local_inventory[1]), str(local_inventory[2]),
                  str(local_inventory[3]), str(local_inventory[4]),
                  str(local_inventory[5])))
    print()
    print("-" * 50)


# Call to main()
if __name__ == "__main__":
    main()
