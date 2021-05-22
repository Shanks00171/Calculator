from tkinter import *

main = Tk()
main.title("Final Simple Calculator")
main.geometry("200x420")

topFrame = LabelFrame(main,text = "Calculator.sht",fg="Green")
topFrame.pack(side=TOP,anchor=S)

# Adding the functions for the calcultor.... The comments in after each function can be used to debug the function
s = [0]
result = 0

# Whenever the '+' button is pressed
def add():
    global s,result
    temp = e.get()
    if temp == "":
        e.insert(0,sum(s))
    else:
        s.append(int(temp))
        result = sum(s)
    e.delete(0,END)
#     print("list - {l}, result - {r}".format(l=s,r=result))


# Whenever the '=' Button is pressed

def eq():
    global result,s
    rough = e.get()
    if result==0 and rough=="":
        result = sum(s)
    if rough!="":
        s.append(int(rough))
        result = sum(s)
    e.delete(0,END)
    e.insert(END,result)
#     print("list - {l}, result - {r}".format(l=s,r=result))

# Whenever the Delete Button is pressed

def det():
    rough = e.get()
    rough = rough[0:-1]
    e.delete(0,END)
    e.insert(END,rough)
#     print("list - {l}, result - {r}".format(l=s,r=result))
    
    
# Whenever the Clear button is pressed
def clearB():
    global s,result
    s.clear()
    result=0
    e.delete(0,END)
#     print("list - {l}, result - {r}".format(l=s,r=result))

# Whenever any number is pressed

def numButton(n):
    e.insert(END,n)
#     print("list - {l}, result - {r}".format(l=s,r=result))

# The entry field of the calculator

e=Entry(topFrame,width=31,bd=5)
e.grid(row=0,column=0,columnspan=4)

# Defining the buttons
clearButton = Button(topFrame,text="Clear",padx=14,pady=25,command=clearB)
addButton = Button(topFrame,text="+",padx=24,pady=25,command = add)
button = list()
button.append(Button(topFrame,text=0,padx=25,pady=25,command=lambda:numButton(str(0))))
button.append(Button(topFrame,text=1,padx=25,pady=25,command=lambda:numButton(str(1))))
button.append(Button(topFrame,text=2,padx=25,pady=25,command=lambda:numButton(str(2))))
button.append(Button(topFrame,text=3,padx=25,pady=25,command=lambda:numButton(str(3))))
button.append(Button(topFrame,text=4,padx=25,pady=25,command=lambda:numButton(str(4))))
button.append(Button(topFrame,text=5,padx=25,pady=25,command=lambda:numButton(str(5))))
button.append(Button(topFrame,text=6,padx=25,pady=25,command=lambda:numButton(str(6))))
button.append(Button(topFrame,text=7,padx=25,pady=25,command=lambda:numButton(str(7))))
button.append(Button(topFrame,text=8,padx=25,pady=25,command=lambda:numButton(str(8))))
button.append(Button(topFrame,text=9,padx=25,pady=25,command=lambda:numButton(str(9))))
equalsButton=Button(topFrame,text="=",padx=40,pady=25,command=eq)
deletePrev = Button(topFrame,text="Delete",padx=35,pady=25,command=det)

# Adding the button on the screens
counter = 1
for k in range(1,4):
    for j in range(1,4):
        button[counter].grid(row=k,column=j)
        counter+=1
        
equalsButton.grid(row=5,column=2,columnspan=2,sticky=E)
button[0].grid(row=4,column=1)
addButton.grid(row=4,column=2)
clearButton.grid(row=4,column=3)
deletePrev.grid(row=5,column=1,columnspan=2,sticky=W)

# keeping the code active
mainloop()