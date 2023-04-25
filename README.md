# currency-converter
from tkinter import *
from tkinter import ttk
from tkinter import messagebox

def center(win):
	win.update_idletasks()
	width = win.winfo_width()
	height = win.winfo_height()
	x = (win.winfo_screenwidth() // 2) - (width // 2)
	y = (win.winfo_screenheight() // 2) - (height // 2)
	win.geometry('{}x{}+{}+{}'.format(width, height, x, y))

def konvert():
	val2.delete(0, END)
	a=float( val1.get() ) #получаем значение из поля1 
	b=com.get() #первый комбобокс
	d=com2.get() #второй комбобокс
	if b=='USD' and d!='USD': # если конвертим из USD
		if d=='EUR': res=a*(USD/EUR)
		if d=='UAN': res=a*(USD/UAN)
		if d=='RUB': res=a*(USD/RUB)
	if b=='EUR' and d!='EUR': # если конвертим из EUR
		if d=='USD': res=a*(EUR/USD)
		if d=='UAN': res=a*(EUR/UAN)
		if d=='RUB': res=a*(EUR/RUB)		
	if b=='UAN' and d!='UAN': # если конвертим из UAN
		if d=='USD': res=a*(UAN/USD)
		if d=='EUR': res=a*(UAN/EUR)
		if d=='RUB': res=a*(UAN/RUB)
	if b=='RUB' and d!='RUB': # если конвертим из RUB
		if d=='USD': res=a*(RUB/USD)
		if d=='EUR': res=a*(RUB/EUR)
		if d=='UAN': res=a*(RUB/UAN)
	res=round(res,3) #округляем res до 3 знаков после запятой
	val2.insert(0 , res) #выводим результат в поле 2

	
window = Tk() #создание окна
window.title('Konvert') #изменяем заголовок
window.geometry('500x300')
center(window)
window.resizable(False, False)

USD=73.0 # курс доллара
EUR=90.1 # курс евро
UAN=11.4 # курс юань
RUB=1    # рубль
VAL=['USD','EUR','UAN' ,'RUB'] #список валют

Label(window, text='Конвертор валют' , font='Times 30').pack()
Label(window, text='Сумма:',   font='Times 15').place(x=120, y=84)
Label(window, text='Конвертировать в:', font='Times 15').place(x=120, y=150)
Label(window, text='Результат :', font='Times 15').place(x=120, y=200)
Button(window , text='Провести конверт', padx='20', pady='8', bg='#32a893', command=konvert).place(x=200 , y = 250)
#комбобокс 1
com=ttk.Combobox(window, width=10, values=VAL , font='20' ,state='readonly')
com.current(0)
com.place(x=300, y =88)
#поле для ввода 1
val1=Entry(window, width=10)
val1.place(x=200 , y=90)
#комбобокс 2
com2=ttk.Combobox(window, width=10, values=VAL , font='20' ,state='readonly')
com2.current(0)
com2.place(x=300, y =150)
#поле для ввода 2
val2=Entry(window, width=10)
val2.place(x=230 , y=204)
window.mainloop() #отобразить окно
