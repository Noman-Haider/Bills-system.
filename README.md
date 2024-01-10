# Bills-system.
import tkinter as tk
from datetime import datetime

class AttendanceBillSystem:
    def __init__(self, master):
        self.master = master
        self.master.title("Attendance Bill System")

        # Variables
        self.student_name_var = tk.StringVar()
        self.attendance_var = tk.IntVar()
        self.bill_amount_var = tk.StringVar()

        # GUI Components
        tk.Label(master, text="Student Name:").grid(row=0, column=0, padx=10, pady=10)
        self.student_entry = tk.Entry(master, textvariable=self.student_name_var)
        self.student_entry.grid(row=0, column=1, padx=10, pady=10)

        tk.Label(master, text="Attendance (in days):").grid(row=1, column=0, padx=10, pady=10)
        self.attendance_entry = tk.Entry(master, textvariable=self.attendance_var)
        self.attendance_entry.grid(row=1, column=1, padx=10, pady=10)

        self.calculate_bill_button = tk.Button(master, text="Calculate Bill", command=self.calculate_bill)
        self.calculate_bill_button.grid(row=2, column=0, columnspan=2, pady=10)

        tk.Label(master, text="Bill Amount:").grid(row=3, column=0, padx=10, pady=10)
        self.bill_amount_label = tk.Label(master, textvariable=self.bill_amount_var)
        self.bill_amount_label.grid(row=3, column=1, padx=10, pady=10)

    def calculate_bill(self):
        student_name = self.student_name_var.get()
        attendance_days = self.attendance_var.get()

        if student_name and attendance_days is not None:
            # Customize your billing logic here
            # For simplicity, let's assume a fixed rate per day
            rate_per_day = 10
            bill_amount = attendance_days * rate_per_day

            # Display the calculated bill amount
            self.bill_amount_var.set(f"${bill_amount}")

def main():
    root = tk.Tk()
    app = AttendanceBillSystem(root)
    root.mainloop()

if __name__ == "__main__":
    main()
