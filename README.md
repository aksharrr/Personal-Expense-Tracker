# Personal-Expense-Tracker
import csv
import datetime

class ExpenseTracker:
    def __init__(self, file_name="expenses.csv"):
        self.file_name = file_name
        self.initialize_file()

    
def initialize_file(self):
        # Create the CSV file with headers if it doesn't exist
        try:
            with open(self.file_name, "x", newline='') as file:
                writer = csv.writer(file)
                writer.writerow(["Date", "Amount", "Category", "Description"])
        except FileExistsError:
            pass
    def add_expense(self, amount, category, description):
        date = datetime.date.today().strftime("%Y-%m-%d")
        with open(self.file_name, "a", newline='') as file:
            writer = csv.writer(file)
            writer.writerow([date, amount, category, description])
        print("Expense added successfully.")
    def view_expenses(self):
        try:
            with open(self.file_name, "r") as file:
                reader = csv.reader(file)
                for row in reader:
                    print(row)
        except FileNotFoundError:
            print("No expenses found.")
    def monthly_summary(self, month, year):
        total = 0
        category_totals = {}
        try:
            with open(self.file_name, "r") as file:
                reader = csv.DictReader(file)
                for row in reader:
                    date = datetime.datetime.strptime(row["Date"], "%Y-%m-%d")
                    if date.month == month and date.year == year:
                        amount = float(row["Amount"])
                        total += amount
                        category = row["Category"]
                        category_totals[category] = category_totals.get(category, 0) + amount

   print(f"\nSummary for {month}/{year}:")
            print(f"Total expenses: ${total:.2f}")
            for category, amount in category_totals.items():
                print(f"{category}: ${amount:.2f}")
        except FileNotFoundError:
            print("No expenses found.")

if __name__ == "__main__":
    tracker = ExpenseTracker()

  while True:
        print("\nOptions:")
        print("1. Add an expense")
        print("2. View all expenses")
        print("3. Monthly summary")
        print("4. Exit")
     choice = input("Choose an option: ")
        if choice == "1":
            amount = input("Enter amount: ")
            category = input("Enter category: ")
            description = input("Enter description: ")
            try:
                tracker.add_expense(float(amount), category, description)
            except ValueError:
                print("Invalid amount. Please enter a number.")
        elif choice == "2":
            tracker.view_expenses()
        elif choice == "3":
            month.   int(input("Enter month (1-12): "))
            year = int(input("Enter year (e.g., 2023): "))
            tracker.monthly_summary(month, year)
        elif choice == "4":
            break
       else:
           
print("Invalid option. Please try again.")
