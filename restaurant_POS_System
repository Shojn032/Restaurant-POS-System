import os
import ast
from google.colab import drive
drive.mount('contentdrive')
CASHIER_FILE = 'contentdriveMyDrivePOS COPYCopy of cashiers.txt'
CATEGORY_FILE = 'contentdriveMyDrivePOS COPYCopy of categories.txt'
RECEIPT_FILE = 'contentdriveMyDrivePOS COPYCopy of reciept.txt'
MEAL_FILE = 'contentdriveMyDrivePOS COPYCopy of meals.txt'
ADMIN_PASSWORD = 'admin123'
def admin_login()
  password = input(Enter Admin Password )
  if password == ADMIN_PASSWORD
    return True
  else
    print()
    print(----10)
    print(Incorrect Password!)
    return False

def load_cashiers()
    accounts = {}
    if os.path.exists(CASHIER_FILE)
        with open(CASHIER_FILE, 'r') as file
            for line in file
                line = line.strip()
                if line
                    try
                        account = ast.literal_eval(line)
                        if isinstance(account, dict) and 'Username' in account
                            accounts[account['Username'].lower()] = account  # Store username in lowercase
                        else
                            print(fSkipping invalid account format {line})
                    except (ValueError, SyntaxError) as e
                        print(fError parsing line as dictionary {line})
    return accounts

def save_cashiers(accounts)
    with open(CASHIER_FILE, 'w') as file
        for username, info in accounts.items()
            file.write(f{info}n)  # Write each account dictionary as a line
# ADD CASHIER FUNCTION
def add_cashier(accounts)#COMPLETEDFINISHED FUNCTION.
    continue_adding = True
    while continue_adding
        print(n)
        username = input(Enter Username for the cashier ).strip().lower()
        if username in accounts
            print(Username already exists! Try a different one.)
        elif not username.isalnum()  # Check for only alphanumeric characters, MEANING ANI IT WILL CHECK IF NAA BAY SPECIAL CHARACTER LIKE(-@#)
            print(Invalid username! Use only letters and numbers (no spaces or special characters).)  #AND DILI SIYA MO ACCEPT IF NAAY SPECIAL CHARACTERS!!
        else
            first_name = input(Enter First Name ).strip().lower()
            last_name = input(Enter Last Name ).strip().lower()
            password = input(Enter Password ).strip()
            accounts[username] = {
                Username username,
                First_Name first_name,
                Last_Name last_name,
                Password password
            }
            save_cashiers(accounts)
            print()
            print(----  10)
            print(fCashier account created for {first_name} {last_name})
            print(----  10)
        # loop until valid input is entered
        while True
                choice = input(nEnter '1' to Add another Cashier or '0' to return to View and Edit Cashier Menu ).strip()
                if choice == '1'
                    continue_adding = True
                    break
                elif choice == '0'
                    print(Returning to the View and Edit Cashier Menu.)
                    continue_adding = False
                    break
                else
                    print(Invalid option! Please enter '1' to add another cashier or '0' to return to the menu.)
def edit_username_cashier(accounts, username)
    new_username = input(Enter new Username ).strip().lower()
    if new_username and new_username != username
        if new_username in accounts
            print(Username already exists! Please choose a different one.)
        elif not new_username.isalnum()
            print(Invalid username! Use only letters and numbers (no spaces or special characters).)
        else
            # Update username key
            accounts[new_username] = accounts.pop(username)
            accounts[new_username]['Username'] = new_username
            print()
            print(----10)
            print(fUpdated Username to {new_username})
            print(Username updated successfully.)
            print(----10)
            return new_username  # Return the updated username
    else
        print(Invalid entry or username is the same as before.)
    return username  # Return the original username if no change
def edit_cashier(accounts)
    while True
        username = input(nEnter the Username of the cashier to edit (or type '0' to cancel) ).strip().lower()
        if username == '0'
            print(nReturning to the View and Edit Cashier Menu.)
            break
        if username in accounts
            print(fnEditing details for cashier '{username}')
            # Show current details
            current_info = accounts[username]
            print(fn1. Username {username})
            print(f2. First Name {current_info['First_Name']})
            print(f3. Last Name {current_info['Last_Name']})
            print(f4. Password {current_info['Password']})
            print(0. To Cancel)
            # Prompt for which field to edit
            while True
                choice = input(nEnter the Number of the detail you want to Edit ).strip()
                if choice == '1'
                  # Update the username if changed
                    updated_username = edit_username_cashier(accounts, username)
                    if updated_username != username
                        username = updated_username  # Update the local username for further edits
                        break  # Re-prompt for cashier to edit
                if choice == '2'
                    new_first_name = input(Enter new First Name ).strip().lower()
                    if new_first_name
                        accounts[username]['First_Name'] = new_first_name
                        print()
                        print(----  10)
                        print(fFirst Name updated to {new_first_name})
                        print(First Name updated successfully.)
                        print(----  10)
                        print()
                elif choice == '3'
                    new_last_name = input(Enter new Last Name ).strip().lower()
                    if new_last_name
                        accounts[username]['Last_Name'] = new_last_name
                        print()
                        print(----  10)
                        print(fLast Name updated to {new_last_name})
                        print(Last Name updated successfully.)
                        print(----  10)
                        print()
                elif choice == '4'
                    new_password = input(Enter new Password ).strip()
                    if new_password
                        accounts[username]['Password'] = new_password
                        print()
                        print(----  10)
                        print(fPassword updated to {new_password})
                        print(Password updated successfully.)
                        print(----  10)
                        print()
                elif choice == '0'
                    print()
                    print(----  10)
                    print(Action canceled)
                    print(Returning to the View and Edit Cashier Menu.)
                    print(----  10)
                    break

                else
                    print(Invalid option! Please select 1, 2, 3, or 4.)

                # Save updates to the file after each edit
                save_cashiers(accounts)

            # Exit the username prompt loop after editing is complete
            break
        else
            print(-------10)
            print(Cashier not found! Please enter a valid Username or type '0' to cancel.)
            print(-------10)
def remove_cashier(accounts)
    while True
        username = input(Enter the Username of the cashier to delete (or type '0' to cancel) ).strip().lower()

        if username == '0'  # Allow user to exit by entering '0'
            print(nReturning to the View and Edit Cashier menu.)
            break
        if username in accounts
            del accounts[username]  # Delete the cashier from accounts
            save_cashiers(accounts)  # Save updated accounts to the file
            print()
            print(----  10)
            print(fCashier '{username}' has been removed.)
            print(----  10)
            # Ask if they want to remove another cashier
            choice = input(nEnter '1' to Remove another Cashier'0' to return to View and Edit Cashier Menu ).strip().lower()
            if choice != '1'  # If the choice is not '1', exit the function
                print()
                print(----  10)
                print(nReturning to the View and Edit Cashier menu.)
                print(----  10)
                break
        else
            print(nCashier not found! Please enter a valid Username or type '0' to cancel.)
# challenging but lingaw ni na function ay
def view_and_edit_cashiers(accounts)  # COMPLETEDFINISHED FUNCTION.
    while True
        print(n CURRENT CASHIERS )
        if accounts
            for username, details in accounts.items()
                print(fUsername {username}, Name {details['First_Name']} {details['Last_Name']}, Password {details['Password']})
        else
            print(No cashiers found.)
        # Prompt for deletion or exit
        print(n)
        print(1. Add a Cashier)
        print(2. Edit a Cashier's Information)
        print(3. Remove a Cashier)
        print(4. Return to Admin Menu)
        print()
        # Loop for valid action choice
        while True
            action = input(nChoose an Action  ).strip()
            if action in {'1', '2', '3', '4'}
                break
            else
                print(Invalid option! Please try again.)
        if action == '1'
            add_cashier(accounts)
        elif action == '2'
            edit_cashier(accounts)
        elif action == '3'
            remove_cashier(accounts)
        elif action == '4'
            print(nExiting View and Edit Cashier Menu...)
            break
def load_categories()
    categories = {}
    if os.path.exists(CATEGORY_FILE)
        with open(CATEGORY_FILE, 'r') as file
            for line in file
                line = line.strip()
                if line
                    try
                        category = ast.literal_eval(line)
                        if isinstance(category, dict) and 'Category' in category
                            categories[category['Category'].lower()] = category
                        else
                            print(fSkipping invalid category format {line})
                    except (ValueError, SyntaxError) as e
                        print(fError parsing line as dictionary {line})
    return categories
# Function to add a category
def add_category(categories)
    while True
        category_name = input(Enter category name to add ).strip().lower()
        
        if category_name in categories
            print(Category already exists! Try a different name.)
        else
            categories[category_name] = {}
            print(fCategory '{category_name}' added successfully!)
        
        choice = input(nEnter '1' to Add another Category or '0' to return to View and Edit Category Menu ).strip()
        if choice == '1'
            continue  # Continue adding categories
        elif choice == '0'
            print(Returning to the View and Edit Category Menu.)
            break
        else
            print(Invalid option! Please enter '1' to add another category or '0' to return to the menu.)
# Function to edit a category
def edit_category(categories)
    while True
        category_name = input(Enter the category name to edit (or type '0' to cancel) ).strip().lower()       
        if category_name == '0'
            print(nReturning to the View and Edit Category Menu.)
            break
        if category_name in categories
            print(fnEditing details for category '{category_name}')
            
            # Show current category details
            print(fCategory {category_name})
            
            # Allow for category renaming
            new_category_name = input(fEnter new name for '{category_name}' (or press enter to keep) ).strip().lower()
            if new_category_name and new_category_name != category_name
                categories[new_category_name] = categories.pop(category_name)
                print(fCategory '{category_name}' renamed to '{new_category_name}'.)               
            break  # Exit after editing        
        else
            print(fCategory '{category_name}' not found! Please enter a valid category name.)
# Function to remove a category
def remove_category(categories)
    while True
        category_name = input(Enter the category name to remove (or type '0' to cancel) ).strip().lower()
        
        if category_name == '0'
            print(nReturning to the View and Edit Category Menu.)
            break
        
        if category_name in categories
            del categories[category_name]  # Remove category
            print(fCategory '{category_name}' has been removed.)
            break
        else
            print(fCategory '{category_name}' not found! Please enter a valid category name.)

# Function to add a mealitem to a category
def add_meal_to_category(categories)
    while True
        category_name = input(Enter category to add mealitem to (Meals, Add-ons, Drinks) ).strip().lower()
        
        if category_name in categories
            meal_name = input(Enter mealitem name ).strip().lower()
            meal_price = float(input(Enter price for this item ).strip())
            
            if meal_name in categories[category_name]
                print(fItem '{meal_name}' already exists in '{category_name}'. Try a different name.)
            else
                categories[category_name][meal_name] = meal_price
                print(fItem '{meal_name}' with price ₱{meal_price.2f} added to '{category_name}'!)
            
            choice = input(nEnter '1' to Add another Item or '0' to return to View and Edit Meal Menu ).strip()
            if choice == '1'
                continue  # Continue adding items
            elif choice == '0'
                print(Returning to the View and Edit Meal Menu.)
                break
            else
                print(Invalid option! Please enter '1' to add another item or '0' to return to the menu.)
        else
            print(fCategory '{category_name}' not found! Please enter a valid category.)
# Function to edit a mealitem in a category
def edit_meal_in_category(categories)
    while True
        category_name = input(Enter category to edit mealitem from (Meals, Add-ons, Drinks) ).strip().lower()        
        if category_name in categories
            meal_name = input(Enter mealitem name to edit ).strip().lower()            
            if meal_name in categories[category_name]
                new_price = float(input(fEnter new price for '{meal_name}' ).strip())
                categories[category_name][meal_name] = new_price
                print(fItem '{meal_name}' price updated to ₱{new_price.2f}.)                
                choice = input(nEnter '1' to Edit another Item or '0' to return to View and Edit Meal Menu ).strip()
                if choice == '1'
                    continue  # Continue editing items
                elif choice == '0'
                    print(Returning to the View and Edit Meal Menu.)
                    break
                else
                    print(Invalid option! Please enter '1' to edit another item or '0' to return to the menu.)
            else
                print(fItem '{meal_name}' not found in '{category_name}'.)
        else
            print(fCategory '{category_name}' not found! Please enter a valid category.)
# Function to remove a mealitem from a category
def remove_meal_from_category(categories)
    while True
        category_name = input(Enter category to remove mealitem from (Meals, Add-ons, Drinks) ).strip().lower()        
        if category_name in categories
            meal_name = input(Enter mealitem name to remove ).strip().lower()          
            if meal_name in categories[category_name]
                del categories[category_name][meal_name]
                print(fItem '{meal_name}' has been removed from '{category_name}'.)               
                choice = input(nEnter '1' to Remove another Item or '0' to return to View and Edit Meal Menu ).strip()
                if choice == '1'
                    continue  # Continue removing items
                elif choice == '0'
                    print(Returning to the View and Edit Meal Menu.)
                    break
                else
                    print(Invalid option! Please enter '1' to remove another item or '0' to return to the menu.)
            else
                print(fItem '{meal_name}' not found in '{category_name}'.)
        else
            print(fCategory '{category_name}' not found! Please enter a valid category.)
def manage_meals(categories)
    while True
        print(n MealItem Management )
        print(1. Add MealItem)
        print(2. Edit MealItem)
        print(3. Remove MealItem)
        print(4. Return to Admin Menu)
        meal_action = input(Choose an action )
        if meal_action == '1'
            add_meal_to_category(categories)
        elif meal_action == '2'
            edit_meal_in_category(categories)
        elif meal_action == '3'
            remove_meal_from_category(categories)
        elif meal_action == '4'
            print(Returning to Admin Menu...)
            break
        else
            print(Invalid option! Please try again.)
def view_sales(total_sales) # to be change into shows all instead of sales, also shows the revenue per cashier
        print(fTotal sales for the day ${total_sales.2f})
def validate_cashier(accounts) #COMPLETEDFINISHED FUNCTION.
    while True
        username = input(nEnter Cashier Username ).strip().lower()
        if username in accounts
            while True  # Loop until the correct password is entered
                password = input(Enter password ).strip()
                if password == accounts[username]['Password']
                    print(n)
                    print(-----------------------------------------------------------)
                    print(f                      WELCOME, {accounts[username]['First_Name'].upper()}!)
                    print(-----------------------------------------------------------)
                    return username
                else
                    print()
                    print(----10)
                    print(Incorrect password! Please try again.)
                    print(----10)
                    print()
        else
            print()
            print(----10)
            print(Cashier not found!)
            print(Please enter an existing cashier Username.)
            print(----10)
def add_item(order, menu) #to be change
    category = input(Enter category (Meals, Add-ons, Drinks) ).strip()
    if category in menu
        item = input(Enter meal name to add ).strip()
        if item in menu[category]
            order[item] = menu[category][item]
            print(f{item} added to the order at ₱{menu[category][item].2f})
        else
            print(Item not found in the selected category!)
    else
        print(Invalid category!)
def remove_item(order)
    meal = input(Enter meal name to remove ).strip()
    if meal in order
        del order[meal]
        print(f{meal} removed from the order.)
    else
        print(Meal not in the order!)
def confirm_order(order)
    if not order
        print(Order is empty!)
        return
    total_price = sum(order.values())
    print(nYour Order Summary)
    for meal, price in order.items()
        print(f{meal} - ₱{price.2f})
    print(fnTotal Amount ₱{total_price.2f})
    return total_price

def cashier_menu(username, total_sales) # shows all instead of the choosen one
    order = {}
    all_meals_data = load_meals()
    while True
        display_menu(all_meals_data)
        print(n Cashier Menu )
        print(1. Add Item)
        print(2. Remove Item)
        print(3. Confirm Order)
        print(4. Exit)
        action = input(Choose an action )
        if action == '1'
            add_item(order, all_meals_data)
        elif action == '2'
            remove_item(order)
        elif action == '3'
            total = confirm_order(order)
            if total
                total_sales += handle_payment(total)
            break
        elif action == '4'
            print(Exiting cashier menu...)
            break
        else
            print(Invalid option! Try again.)
    return total_sales

def display_menu(meals)
    # Display the menu items in a format similar to 'view and edit cashiers'.
    print(nNiko Chicks Menu)
    for category, items in meals.items()
        print(fn{category.upper()})
        for item, price in items.items()
            print(fItem {item}, Price ₱{price.2f})
def handle_payment(total)
    print(Payment Options)
    print(1. Cash)
    print(2. Credit)
    payment_method = input(Choose payment method )
    if payment_method in ['1', '2']
        print(fPayment of ₱{total.2f} processed.)
    else
        print(Invalid payment option!)
    return total
def admin_menu(accounts, categories, meals_items, total_sales)
    while True
        print(n[---------------------- Admin Menu -------------------------])
        print(1. View and Edit Cashiers)
        print(2. View and Edit Category)
        print(3. View and Edit MealItem)
        print(4. View Total Sales)
        print(5. Exit)
        action = input(Choose an action )
        if action == '1'
            view_and_edit_cashiers(accounts)
        elif action == '2'
            # Category Management
            print(n Category Management )
            print(1. Add Category)
            print(2. Edit Category)
            print(3. Remove Category)
            print(4. Return to Admin Menu)
            category_action = input(Choose an action )
            if category_action == '1'
                add_category(categories)
            elif category_action == '2'
                edit_category(categories)
            elif category_action == '3'
                remove_category(categories)
            elif category_action == '4'
                continue
            else
                print(Invalid option! Please try again.)
        elif action == '3'
            manage_meals(categories)  # Call the manage_meals function here
        elif action == '4'
            view_sales(total_sales)
        elif action == '5'
            print(Exiting admin menu...)
            break
        else
            print(nInvalid option! Try again.)
def pos_system()  # UPDATED BY NIMROD
    accounts = load_cashiers()
    categories = load_categories()  # Changed 'menu' to 'categories'
    meals_items = load_meals()
    total_sales = 0
    while True
        print(n[------------------ Restaurant POS System ------------------])
        print(1. Cashier)
        print(2. Admin)
        print(3. Exit)
        choice = input(Select an Option ).strip().lower()
        if choice == '1'
            username = validate_cashier(accounts)
            if username
                total_sales = cashier_menu(username, total_sales)
        elif choice == '2'
            if admin_login()  # GI BALHIN NKO ANG LOGIN DIRI
                admin_menu(accounts, categories, meals_items, total_sales)  # Now 'categories' is defined
            else
                print(Access Denied. Returning to Main Menu...)
                print(----  10)
        elif choice == '3'
            print(Exiting POS system...)
            break
        else
            print(Invalid option! Try again.)
pos_system()
