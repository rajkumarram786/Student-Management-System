# Student-Management-System
#Student management system layout in python 
from tkinter import *
from tkinter import ttk
import pymysql


class Student:
    def __init__(self, root):
        self.root = root
        self.root.title("Student Management System")
        self.root.geometry("1350x700+0+0")

        title = Label(self.root, text="Student Management System", bd=10, relief=GROOVE,
                      font=("times new roman ", 40, "  bold"), bg="yellow", fg="red")
        title.pack(side=TOP, fill=X)

        # ==================Manage Frame=======================

        Manage_Frame = Frame(self.root, bd=4, relief=RIDGE, bg="crimson")
        Manage_Frame.place(x=20, y=100, width=450, height=600)

        # ==================Details  Frame=======================

        Details_Manage_Frame = Frame(self.root, bd=4, relief=RIDGE, bg="crimson")
        Details_Manage_Frame.place(x=500, y=100, width=750, height=560)

        m_title = Label(Manage_Frame, text="Manage Student", bg="crimson", fg="white",
                        font=("times new roman ", 30, "bold"))
        m_title.grid(row=0, columnspan=2, pady=20)

        # ==================ROLL NO.=======================

        lbl_roll = Label(Manage_Frame, text="Roll No.", bg="crimson", fg="white", font=("times new roman ", 20, "bold"))
        lbl_roll.grid(row=1, column=0, pady=10, padx=20, sticky="w")

        text_Roll = Entry(Manage_Frame, font=("times new roman ", 15, "bold"), bd=5, relief=GROOVE)
        text_Roll.grid(row=1, column=1, pady=10, padx=20, sticky="w")

        #  ========================================================= NAME ==============================

        lbl_roll = Label(Manage_Frame, text="Name", bg="crimson", fg="white", font=("times new roman ", 20, "bold"))
        lbl_roll.grid(row=2, column=0, pady=10, padx=20, sticky="w")
        text_Roll = Entry(Manage_Frame, font=("times new roman ", 15, "bold"), bd=5, relief=GROOVE)
        text_Roll.grid(row=2, column=1, pady=10, padx=20, sticky="w")

        #  =========================================Email.=======================
        lbl_roll = Label(Manage_Frame, text="Email", bg="crimson", fg="white", font=("times new roman ", 20, "bold"))
        lbl_roll.grid(row=3, column=0, pady=10, padx=20, sticky="w")
        text_Roll = Entry(Manage_Frame, font=("times new roman ", 15, "bold"), bd=5, relief=GROOVE)
        text_Roll.grid(row=3, column=1, pady=10, padx=20, sticky="w")

        #   ================================ Gender.=======================\

        lbl_roll = Label(Manage_Frame, text="Gender", bg="crimson", fg="white", font=("times new roman ", 20, "bold"))
        lbl_roll.grid(row=4, column=0, pady=10, padx=20, sticky="w")

        combo_gender = ttk.Combobox(Manage_Frame, font=("times new roman", 15, "bold"), state="readonly")
        combo_gender["values"] = ("Male", "Female", "Other")
        combo_gender.grid(row=4, column=1, padx=20, pady=10)

        # ===================================CONTACT=======================
        lbl_roll = Label(Manage_Frame, text="Contact", bg="crimson", fg="white", font=("times new roman ", 20, "bold"))
        lbl_roll.grid(row=5, column=0, pady=10, padx=20, sticky="w")
        text_Roll = Entry(Manage_Frame, font=("times new roman ", 15, "bold"), bd=5, relief=GROOVE)
        text_Roll.grid(row=5, column=1, pady=10, padx=20, sticky="w")

        #  ===================================D.O.B======================
        lbl_roll = Label(Manage_Frame, text="D.O.B", bg="crimson", fg="white", font=("times new roman ", 20, "bold"))
        lbl_roll.grid(row=6, column=0, pady=10, padx=20, sticky="w")
        text_Roll = Entry(Manage_Frame, font=("times new roman ", 15, "bold"), bd=5, relief=GROOVE)
        text_Roll.grid(row=6, column=1, pady=10, padx=20, sticky="w")

        # ================================= Address.=======================
        lbl_Address = Label(Manage_Frame, text="Address", bg="crimson", fg="white",
                            font=("times new roman ", 20, "bold"))
        lbl_Address.grid(row=7, column=0, pady=10, padx=20, sticky="w")

        txt_Address = Text(Manage_Frame, width=30, height=4, font=("", 10))
        txt_Address.grid(row=7, column=1, pady=10, padx=20, sticky="w")

        # ==================BUTTON frame==================
        btn_Frame = Frame(Manage_Frame, bd=4, relief=RIDGE, bg="crimson")
        btn_Frame.place(x=10, y=525, width=420)

        Add_Btn = Button(btn_Frame, text="Add", width=10).grid(row=0, column=0, padx=10, pady=10)
        Update_Btn = Button(btn_Frame, text="Update ", width=10).grid(row=0, column=1, padx=10, pady=10)
        Delete_Bnt = Button(btn_Frame, text=" Delete", width=10).grid(row=0, column=2, padx=10, pady=10)
        ClearBtn = Button(btn_Frame, text="Clear", width=10).grid(row=0, column=3, padx=10, pady=10)

        # =================Details frame==================
        Details_Frame = Frame(self.root, bd=4, relief=RIDGE, bg="crimson")
        Details_Frame.place(x=500, y=100, width=800, height=580)

        # =================Search label==================

        lbl_Search = Label(Details_Frame, text="Search By", bg="crimson", fg="white",
                           font=("times new roman ", 20, "bold"))
        lbl_Search.grid(row=0, column=0, pady=10, padx=20, sticky="w")

        combo_gender = ttk.Combobox(Details_Frame, font=("times new roman", 13, "bold"), state="readonly")
        combo_gender["values"] = ("Roll", "Name", "Contact")
        combo_gender.grid(row=0, column=1, padx=20, pady=10)

        # =================Entry Search BUTTON==================

        text_Search = Entry(Details_Frame,width=15, font=("times new roman ", 10, "bold"), bd=5, relief=GROOVE)
        text_Search.grid(row=0, column=2, pady=10, padx=20, sticky="w")

        Search_btn = Button(Details_Frame, text="Search", width=10, pady=5).grid(row=0, column=3, padx=10, pady=10)
        ShowAll_btn = Button(Details_Frame, text="Show All", width=10, pady=5).grid(row=0, column=4, padx=10, pady=10)

        # =================Table Frame==================
        Table_Frame = Frame(Details_Frame, bd=4, relief=RIDGE, bg="crimson")
        Table_Frame.place(x=10, y=70, width=760, height=500)

        scroll_x = Scrollbar(Table_Frame, orient=HORIZONTAL)
        scroll_y = Scrollbar(Table_Frame, orient=VERTICAL)

        Student_table = ttk.Treeview(Table_Frame, columns=("roll", "Name", "email", "gender", "contact", "dob", "Address"), xscrollcommand=scroll_x.set, yscrollcommand=scroll_y.set)
        scroll_x.pack(side=BOTTOM, fill=X)
        scroll_y.pack(side=RIGHT, fill=Y)
        scroll_x.config(command=Student_table.xview)
        Student_table.heading("roll", text="Roll No.")
        Student_table.heading("Name", text="Name")
        Student_table.heading("email", text="Email")
        Student_table.heading("gender", text="Gender")
        Student_table.heading("contact", text="CONTACT")
        Student_table.heading("dob", text="D.O.B")
        Student_table.heading("Address", text=" Address")
        # Student_table["Show"]="heading"
        Student_table.column("roll", width=100)
        Student_table.column("Name", width=100)
        Student_table.column("email", width=100)
        Student_table.column("gender", width=100)
        Student_table.column("contact", width=100)
        Student_table.column("Address", width=150)
        Student_table.pack(fill=BOTH, expand=1)


    # def_add_student(self):


root = Tk()
ob = Student(root)

root.mainloop()

