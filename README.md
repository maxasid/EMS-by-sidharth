# EMS-by-sidharth
class employee:
       def __init__(self, emp_id, name, age, department, salary):
        self.emp_id = emp_id
        self.name = name
        self.age = age
        self.department = department
        self.salary = salary
class employee_management_system(employee):
    def __init__(self):
        self.employees = {
            101: employee(101, 'Satya', 27, 'HR', 50000),
            102: employee(102, 'Ravi', 30, 'IT', 60000),
            103: employee(103, 'Anjali', 25, 'Marketing', 55000)
        }
    def main_menu(self):
        while True:
            print("\n=== Employee Management System ===")
            print("1. Add Employee")
            print("2. View All Employees")
            print("3. Search for Employee")
            print("4. Exit")
            choice = input("Enter your choice (1-4): ")
            if choice == '1':
                self.add_employee()
            elif choice == '2':
                self.view_employees()
            elif choice == '3':
                self.search_employee()
            elif choice == '4':
                print("Thank you for using the EMS. Goodbye!")
                break
            else:
                print("Invalid choice. Please try again.")
    def add_employee(self):
        try:
            emp_id = int(input("Enter Employee ID: "))
            if emp_id in self.employees:
                print("This Employee ID already exists.")
                return
            name = input("Enter Name: ")
            age = int(input("Enter Age: "))
            department = input("Enter Department: ")
            salary = float(input("Enter Salary: "))
            self.employees[emp_id] = employee(emp_id, name, age, department, salary)
            print("✅ Employee added successfully.")
        except ValueError:
            print("Invalid input. Please enter correct data types.")
    def view_employees(self):
        if not self.employees:
            print("No employees available.")
            return
        print("\nEmp_ID   Name            Age   Department      Salary")
        print("-" * 55)
        for emp in self.employees.values():
            print(f"{emp.emp_id:<8} {emp.name:<15} {emp.age:<5} {emp.department:<15} {emp.salary:<10}")
    def search_employee(self):
        try:
            emp_id = int(input("Enter Employee ID to search: "))
            emp = self.employees.get(emp_id)
            if emp:
                print("\nEmployee Found:")
                print(f"Name      : {emp.name}")
                print(f"Age       : {emp.age}")
                print(f"Department: {emp.department}")
                print(f"Salary    : {emp.salary}")
            else:
                print(" Employee not found.")
        except ValueError:
            print("Please enter a valid Employee ID.")
            
if __name__ == "__main__":
    ems = employee_management_system()
    ems.main_menu()
