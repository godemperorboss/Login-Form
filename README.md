# Login-Form
A Login Form which is connected with SQLlite DB Browser by PyCharm 
from tkinter import*
import sqlite3

root=Tk()
root.geometry("800x800")
root.title("Login Page")
root.configure(bg="orange")

username = StringVar()
EMail = StringVar()
Phone = IntVar()
Gender = StringVar()
Place = StringVar()



def Login():
    user = e2.get()
    email = e3.get()
    ph=e4.get()
    gen = Gender.get()
    pl = Place.get()
    conn = sqlite3.connect("login_page.db")
    cursorob = conn.cursor()
    cursorob.execute("create table if not exists form(USERNAME text, EMAIL text, PHONE integer, GENDER text, PLACE text)")
    cursorob.execute("insert into form(USERNAME,EMAIL,PHONE,GENDER,PLACE)VALUES(?,?,?,?,?)",(user,email,ph,gen,pl))
    conn.commit()


l1 = Label(root, text = "LOGIN FORM", font=("Times New Roman", 20, "bold", "underline"), fg= "red", bg= "orange")
l1.place(x=200, y=120)
l2 = Label(root, text = "Username: ", font=("Times New Roman", 12, "bold"), fg= "red", bg= "orange")
l2.place(x=120, y=200)
e2 = Entry(root, width= 20, font=("Times New Roman",15))
e2.place(x=220, y=200)
l3 = Label(root, text = "EMail: ", font=("Times New Roman", 12, "bold"), fg= "red", bg= "orange")
l3.place(x=120, y=250)
e3 = Entry(root, width= 20, font=("Times New Roman",15))
e3.place(x=220, y=250)
l4 = Label(root, text = "Phone: ", font=("Times New Roman", 12, "bold"), fg= "red", bg= "orange")
l4.place(x=120, y=300)
e4 = Entry(root, width= 20, font=("Times New Roman",15))
e4.place(x=220, y=300)
l5 = Label(root, text = "Gender: ", font=("Times New Roman", 12, "bold"), fg= "red", bg= "orange")
l5.place(x=120, y=350)
r5 = Radiobutton(root, text="MALE", variable=Gender, font=("Arial", 12), value="Male", fg="Red", bg="Orange")
r5.place(x=220, y=350)
r6 = Radiobutton(root, text="FEMALE", variable=Gender, font=("Arial", 12), value="Female", fg="Red", bg="Orange")
r6.place(x=320, y=350)
l6 = Label(root, text = "Place: ", font=("Times New Roman", 12, "bold"), fg= "red", bg= "orange")
l6.place(x=120, y=400)
places = ["Thiruvananthapuram", "Kollam", "Alappuzha", "Ernakulam", "Kottayam", "Idukki"]
Place.set(places[0])
Place_dropdown = OptionMenu(root, Place, *places)
Place_dropdown.configure(width=20)
Place_dropdown.place(x=220, y=400)
button = Button(root, text="LOGIN", font=("Times New Roman", 10), width= 20, fg= "yellow", bg="red", activeforeground= "purple", activebackground= "blue", command= Login)
button.place(x=250, y= 480)



root.mainloop()
