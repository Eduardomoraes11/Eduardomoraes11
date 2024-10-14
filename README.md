def add_to_display(value):
    current_text = display_var.get()
    display_var.set(current_text + value)

def clear_display():
    display_var.set("")

def calculate():
    try:
        result = eval(display_var.get())
        display_var.set(str(result))
    except:
        messagebox.showerror("Erro", "Operação inválida!")

root = tk.Tk()
root.title("Calculadora de Gatinhos")
root.geometry("300x400")

cat_img = tk.PhotoImage(file="gatinho.png")  # Insira o caminho da imagem de gatinho aqui
cat_label = tk.Label(root, image=cat_img)
cat_label.grid(row=0, column=0, columnspan=4)

display_var = tk.StringVar()

display = tk.Entry(root, textvariable=display_var, font=("Arial", 20), bd=10, insertwidth=2, width=14, borderwidth=4)
display.grid(row=1, column=0, columnspan=4)

buttons = [
    ('7', 2, 0), ('8', 2, 1), ('9', 2, 2), ('/', 2, 3),
    ('4', 3, 0), ('5', 3, 1), ('6', 3, 2), ('*', 3, 3),
    ('1', 4, 0), ('2', 4, 1), ('3', 4, 2), ('-', 4, 3),
    ('0', 5, 0), ('.', 5, 1), ('+', 5, 2), ('=', 5, 3),
]

for (text, row, col) in buttons:
    if text == "=":
        button = tk.Button(root, text=text, padx=20, pady=20, font=("Arial", 15), command=calculate)
    else:
        button = tk.Button(root, text=text, padx=20, pady=20, font=("Arial", 15), command=lambda t=text: add_to_display(t))
    button.grid(row=row, column=col)

clear_button = tk.Button(root, text="C", padx=20, pady=20, font=("Arial", 15), command=clear_display)
clear_button.grid(row=5, column=2)

root.mainloop()
