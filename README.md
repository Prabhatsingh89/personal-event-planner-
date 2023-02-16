# Import the datetime library to work with dates and times
import datetime

# Create a dictionary to store events and their details
events = {}

# Define a function to add events to the list
def add_event():
    name = input("Enter the name of the event: ")
    date_str = input("Enter the date of the event (in format dd/mm/yyyy): ")
    time_str = input("Enter the time of the event (in 24-hour format HH:MM): ")
    description = input("Enter a description of the event: ")

    # Convert the date and time strings into a datetime object
    date = datetime.datetime.strptime(date_str, '%d/%m/%Y').date()
    time = datetime.datetime.strptime(time_str, '%H:%M').time()

    # Add the event details to the events dictionary
    events[name] = {
        'date': date,
        'time': time,
        'description': description
    }

# Define a function to display the list of events
def list_events():
    if not events:
        print("No events found.")
    else:
        for name, details in events.items():
            print("Event name:", name)
            print("Date:", details['date'])
            print("Time:", details['time'])
            print("Description:", details['description'])
            print()

# Define a function to remove an event from the list
def remove_event():
    name = input("Enter the name of the event you want to remove: ")
    if name in events:
        del events[name]
        print("Event removed successfully.")
    else:
        print("Event not found.")

# Define a function to show a menu of options for the user
def show_menu():
    print("Personal Event Planner")
    print("----------------------")
    print("1. Add an event")
    print("2. List all events")
    print("3. Remove an event")
    print("4. Exit")
    print()

# Main program loop
while True:
    show_menu()
    choice = input("Enter your choice: ")

    if choice == '1':
        add_event()
    elif choice == '2':
        list_events()
    elif choice == '3':
        remove_event()
    elif choice == '4':
        print("Goodbye!")
        break
    else:
        print("Invalid choice. Please try again.")

