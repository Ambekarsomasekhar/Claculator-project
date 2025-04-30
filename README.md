from tkinter import *

window = Tk()
window.title("calculator")


def clear():
    db.delete(0, END)


def bt_clk(num):
    cur_num = db.get()
    db.delete(0, END)
    f_num = cur_num + num
    db.insert(0, f_num)


first_num = 0
math = ''


def calc(math_type):
    global first_num, math
    math = math_type
    first_num = db.get()
    clear()


def equal():
    result = ''
    global first_num
    second_num = db.get()
    clear()
    if math == 'add':
        result = int(first_num) + int(second_num)
    elif math == 'sub':
        result = int(first_num) - int(second_num)
    elif math == 'mul':
        result = int(first_num) * int(second_num)
    elif math == 'divi':
        result = int(first_num) / int(second_num)
    db.insert(0, str(result))


# creating widget
db = Entry(window, width=18, font=('Arial', 28), justify='right')
bt_0 = Button(window, text='0', padx=36, pady=10, font=('Arial', 14), command=lambda: bt_clk('0'))
bt_1 = Button(window, text='1', padx=36, pady=10, font=('Arial', 14), command=lambda: bt_clk('1'))
bt_2 = Button(window, text='2', padx=36, pady=10, font=('Arial', 14), command=lambda: bt_clk('2'))
bt_3 = Button(window, text='3', padx=36, pady=10, font=('Arial', 14), command=lambda: bt_clk('3'))
bt_4 = Button(window, text='4', padx=36, pady=10, font=('Arial', 14), command=lambda: bt_clk('4'))
bt_5 = Button(window, text='5', padx=36, pady=10, font=('Arial', 14), command=lambda: bt_clk('5'))
bt_6 = Button(window, text='6', padx=36, pady=10, font=('Arial', 14), command=lambda: bt_clk('6'))
bt_7 = Button(window, text='7', padx=36, pady=10, font=('Arial', 14), command=lambda: bt_clk('7'))
bt_8 = Button(window, text='8', padx=36, pady=10, font=('Arial', 14), command=lambda: bt_clk('8'))
bt_9 = Button(window, text='9', padx=36, pady=10, font=('Arial', 14), command=lambda: bt_clk('9'))

bt_clear = Button(window, text='clear', padx=86, pady=10, font=('Arial', 14), command=clear)
bt_divi = Button(window, text='/', padx=38, pady=10, font=('Arial', 14), command=lambda: calc('divi'))
bt_mul = Button(window, text='*', padx=38, pady=10, font=('Arial', 14), command=lambda: calc('mul'))
bt_sub = Button(window, text='-', padx=38, pady=10, font=('Arial', 14), command=lambda: calc('sub'))
bt_add = Button(window, text='+', padx=38, pady=10, font=('Arial', 14), command=lambda: calc('add'))
bt_equal = Button(window, text='=', padx=38, pady=40, font=('Arial', 14), command=equal)
# showing widget
bt_clear.grid(row=4, column=1, columnspan=2, padx=2, pady=2)
bt_equal.grid(row=5, column=2, columnspan=2, rowspan=2, padx=2, pady=2)
bt_add.grid(row=5, column=0, padx=2, pady=2)
bt_sub.grid(row=5, column=1, padx=2, pady=2)
bt_divi.grid(row=6, column=0, padx=2, pady=2)
bt_mul.grid(row=6, column=1, padx=2, pady=2)

bt_0.grid(row=4, column=0, padx=2, pady=2)

bt_1.grid(row=3, column=0, padx=2, pady=2)
bt_2.grid(row=3, column=1, padx=2, pady=2)
bt_3.grid(row=3, column=2, padx=2, pady=2)

bt_4.grid(row=2, column=0, padx=2, pady=2)
bt_5.grid(row=2, column=1, padx=2, pady=2)
bt_6.grid(row=2, column=2, padx=2, pady=2)

bt_7.grid(row=1, column=0, padx=2, pady=2)
bt_8.grid(row=1, column=1, padx=2, pady=2)
bt_9.grid(row=1, column=2, padx=2, pady=2)

db.grid(row=0, column=0, columnspan=3, pady=10)
window.mainloop()
