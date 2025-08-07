import tkinter as tk
from tkinter import ttk, messagebox

# Dados iniciais
nomes = ["João", "Julia", "Natan", "Carlos", "Bruno"]
cpfs = ["123.456.789-00", "987.654.321-00", "321.654.987-00", "456.789.123-00", "789.123.456-00"]
emails = ["joao@email.com", "julia@email.com", "natan@email.com", "carlos@email.com", "bruno@email.com"]
telefones = ["(11) 91234-5678", "(21) 99876-5432", "(31) 92345-6789", "(41) 93456-7890", "(51) 94567-8901"]
ids = ["1111-11", "1112-11", "1113-11", "1114-11", "1115-11"]


nomes1 = ['Bruno Richard', 'Davi Souza']
cpfs1 = ['659.557.416-66', '063.577.491-88']
email1 = ['Richard.553@gmail.com', 'dvSouza@gmail.com']
telefones1 = ['(11) 91234-5678', '(31) 94321-9876']
ids1 = ['1111-11', '2222-22']
salario = ['R$1.250,00','R$1.250,00' ]

tprodutos = {
    "C": [
        {"id": "C001", "nome": "Calça", "preco": 500.00, "marca": "Nike"},
        {"id": "C002", "nome": "Calça Jeans Slim", "preco": 289.90, "marca": "Levi's"},
        {"id": "C003", "nome": "Legging Esportiva", "preco": 199.00, "marca": "Lupo"},
        {"id": "C004", "nome": "Calça Jogger Jeans", "preco": 289.90, "marca": "Malwee"},
        ],
    "B": [
        {"id": "B001", "nome": "Blusa", "preco": 475.50, "marca": "Adidas"},
        {"id": "B002", "nome": "Camiseta Estampada", "preco": 129.99, "marca": "Vans"},
        {"id": "B003", "nome": "Regata Esportiva", "preco": 89.90, "marca": "Reebok"},
        {"id": "B004", "nome": "Cropped Fitness", "preco": 109.90, "marca": "Lupo"}
    ],
    "M": [
        {"id": "M001", "nome": "Moletom", "preco": 400.50, "marca": "Adidas"},
        {"id": "M002", "nome": "Jaqueta Corta-Vento", "preco": 599.90, "marca": "Puma"},
        {"id": "M003", "nome": "Cardigan Estiloso", "preco": 299.90, "marca": "Gap"},
        {"id": "M004", "nome": "Casaco de Tricô", "preco": 359.00, "marca": "Hering"},
    ],
    "S": [
        {"id": "S001", "nome": "Camisa Polo", "preco": 249.00, "marca": "Lacoste"},
        {"id": "S002", "nome": "Camisa Social Slim", "preco": 189.50, "marca": "Reserva"},
         {"id": "S003", "nome": "Camisa Estampada", "preco": 179.90, "marca": "Hollister"},
        {"id": "S004", "nome": "Camisa Linho", "preco": 209.00, "marca": "Zara"},
    ],
    "D": [
        {"id": "D001", "nome": "Macacão Feminino", "preco": 349.90, "marca": "Zara"},
        {"id": "D002", "nome": "Vestido Floral", "preco": 289.90, "marca": "Forever 21"},
        {"id": "D003", "nome": "Vestido Midi", "preco": 399.90, "marca": "Farm"},
        {"id": "D004", "nome": "Jardineira Jeans", "preco": 259.90, "marca": "Colcci"},
    ],
    "F": [
        {"id": "F001", "nome": "Tênis Corrida", "preco": 729.00, "marca": "Asics"},
        {"id": "F002", "nome": "Calçado Casual", "preco": 379.00, "marca": "Converse"},
        {"id": "F003", "nome": "Sandália Plataforma", "preco": 219.99, "marca": "Melissa"},
        {"id": "F004", "nome": "Tênis Skate", "preco": 399.90, "marca": "DC Shoes"},
    ],
    "A": [
        {"id": "A001", "nome": "Meia Cano Alto", "preco": 29.99, "marca": "Nike"},
        {"id": "A002", "nome": "Touca de Lã", "preco": 59.90, "marca": "Adidas"},
        {"id": "A003", "nome": "Boné Estilizado", "preco": 89.00, "marca": "New Era"},
        {"id": "A004", "nome": "Cinto de Couro", "preco": 149.90, "marca": "Calvin Klein"},
    ],
    "L": [
        {"id": "L001", "nome": "Blazer Alfaiataria", "preco": 459.00, "marca": "Zara"},
        {"id": "L002", "nome": "Casaco Longo", "preco": 599.90, "marca": "Massimo Dutti"},
        {"id": "L003", "nome": "Colete Social", "preco": 259.90, "marca": "Renner"},
        {"id": "L004", "nome": "Paletó Slim Fit", "preco": 699.90, "marca": "Dudalina"},
    ]
}

vendas = []

class LojaApp(tk.Tk):
    def __init__(self):
        super().__init__()
        self.title("Loja Modularizada")
        self.geometry("700x500")
        self.resizable(False, False)
        self._frame = None
        self.funcionario_tipo = None
        self.switch_frame(MenuInicial)
   def switch_frame(self, frame_class, *args):
        if self._frame is not None:
            self._frame.destroy()
        self._frame = frame_class(self, *args)
        self._frame.pack(fill="both", expand=True)

class MenuInicial(tk.Frame):
        def __init__(self, master):
            super().__init__(master, bg="#2E2E2E") 
            tk.Label(
                self,
                text="SEJA BEM VINDO A NOSSA LOJA",
                font=("Arial", 18),        
                bg="#2e2e2e"         
            ).pack(pady=30)
               tk.Button(
                self,
                text="Cliente",
                width=25,
                height=2,
                bg="#B67C00", 
                command=lambda: master.switch_frame(MenuClienteProdutos)
            ).pack(pady=10)
            tk.Button(
                self,
                text="Funcionário",
                width=25,
                height=2,
                bg="#B67C00", 
                command=lambda: master.switch_frame(LoginFuncionario)
            ).pack(pady=10)
            tk.Button(
                self,
                text="Sair",
                width=25,
                height=2,
                bg="#B67C00",         
                command=master.destroy
            ).pack(pady=10)

class LoginFuncionario(tk.Frame):
    def __init__(self, master):
        super().__init__(master, bg="#2E2E2E")
        tk.Label(self, text="Login Funcionário", font=("Arial", 16),bg="#2e2e2e").pack(pady=20)
        tk.Label(self, text="Senha:",bg="#2e2e2e").pack()
        self.senha_entry = tk.Entry(self, show="*")
        self.senha_entry.pack(pady=5)
        tk.Label(self, text="Tipo do Funcionário:",bg="#2e2e2e").pack()
        self.tipo_combo = ttk.Combobox(self, values=["Vendedor", "Gerente", "RH"], state="readonly")
        self.tipo_combo.pack(pady=5)
        tk.Button(self, text="Entrar", command=self.verificar_login,bg="#B67C00").pack(pady=15)
        tk.Button(self, text="Voltar", command=lambda: master.switch_frame(MenuInicial),bg="#B67C00").pack()
    def verificar_login(self):
        senha = self.senha_entry.get()
        tipo = self.tipo_combo.get()
        # Para simplificar, senha sempre '1234'
        if senha == "1234" and tipo in ["Vendedor", "Gerente", "RH"]:
            self.master.funcionario_tipo = tipo
            self.master.switch_frame(MenuFuncionario)
        else:
            messagebox.showerror("Erro", "Senha ou tipo inválido.")

class MenuFuncionario(tk.Frame):
    def __init__(self, master):
        super().__init__(master, bg="#2E2E2E")
        tipo = master.funcionario_tipo
        tk.Label(self, text=f"Área de Funcionário: {tipo}", font=("Arial", 18), bg="#2E2E2E").pack(pady=20)
        if tipo == "Gerente":
            tk.Button(self, text="Ver Clientes", width=30, height=2, command=lambda: master.switch_frame(MenuClientes),bg="#B67C00").pack(pady=5)
            tk.Button(self, text="Gerenciar Produtos", width=30, height=2, command=lambda: master.switch_frame(GerenciarProdutos),bg="#B67C00").pack(pady=5)
        elif tipo == "Vendedor":
            tk.Button(self, text="Ver Clientes", width=30, height=2, command=lambda: master.switch_frame(MenuClientes), bg="#B67C00").pack(pady=5)
            tk.Button(self, text="Registrar Venda", width=30, height=2, command=lambda: master.switch_frame(RegistrarVenda),bg="#B67C00").pack(pady=5)
        elif tipo == "RH":
            tk.Button(self, text="Ver Funcionários", width=30, height=2, command=lambda: master.switch_frame(MenuFuncionarios), bg="#B67C00").pack(pady=5)
            tk.Button(self, text="Ver Vendas", width=30, height=2, command=lambda: master.switch_frame(RelatorioVendas),bg="#B67C00").pack(pady=5)
        tk.Button(self, text="Logout", width=30, height=2, command=lambda: master.switch_frame(MenuInicial),bg="#B67C00").pack(pady=20)

class MenuClienteProdutos(tk.Frame):
    def __init__(self, master):
        super().__init__(master, bg="#2E2E2E")
        tk.Label(self, text="Produtos Disponíveis", font=("Arial", 16),bg="#2E2E2E").pack(pady=10)
        self.tree = ttk.Treeview(self, columns=("ID", "Nome", "Marca", "Preço"), show="headings")
        for col in ("ID", "Nome", "Marca", "Preço"):
            self.tree.heading(col, text=col)
            self.tree.column(col, width=130)
        self.tree.pack(fill="both", expand=True, padx=10)
        self.atualizar_lista()
        btn_frame = tk.Frame(self, bg="#2E2E2E")
        btn_frame.pack(pady=10)
        tk.Button(btn_frame, text="Comprar Produto", command=self.comprar_produto, bg="#B67C00").pack(side="left", padx=5)
        tk.Button(btn_frame, text="Voltar", command=lambda: master.switch_frame(MenuInicial), bg="#B67C00").pack(side="left", padx=5)
    def atualizar_lista(self):
        self.tree.delete(*self.tree.get_children())
        for cat, produtos in tprodutos.items():
            for p in produtos:
                self.tree.insert("", tk.END, values=(p["id"], p["nome"], p["marca"], f"{p['preco']:.2f}"))
    def comprar_produto(self):
        selecionado = self.tree.selection()
        if not selecionado:
            messagebox.showwarning("Aviso", "Selecione um produto para comprar.")
            return
        item = self.tree.item(selecionado)
        pid = item["values"][0]
        self.master.switch_frame(ComprarProduto, pid)

class ComprarProduto(tk.Frame):
    def __init__(self, master, pid):
        super().__init__(master, bg="#2E2E2E")
        tk.Label(
                self,
                text="FINALIZE SUA COMPRA",
                font=("Arial", 18),          
                bg="#2e2e2e"           
            ).pack(pady=30)
        self.produto = None
        for produtos in tprodutos.values():
            for p in produtos:
                if p["id"] == pid:
                    self.produto = p
                    break
            if self.produto:
                break
        if not self.produto:
            messagebox.showerror("Erro", "Produto não encontrado.")
            master.switch_frame(MenuClienteProdutos)
            return
        tk.Label(self, text=f"Comprar: {self.produto['nome']} (R$ {self.produto['preco']:.2f})", font=("Arial", 16),bg="#2e2e2e").pack(pady=10)
        tk.Label(self, text="Quantidade:", bg="#2e2e2e").pack()
        self.quant_entry = tk.Entry(self)
        self.quant_entry.pack()
        tk.Label(self, text="Nome do Cliente:",bg="#2e2e2e").pack()
        self.nome_entry = tk.Entry(self)
        self.nome_entry.pack()
        tk.Label(self, text="Forma de pagamento:",bg="#2e2e2e").pack()
        self.pag_combo = ttk.Combobox(self, values=["Cartão de crédito", "Cartão de débito", "Dinheiro", "Pix"], state="readonly")
        self.pag_combo.pack()
        tk.Button(self, text="Finalizar Compra", command=self.finalizar_compra, bg="#B67C00").pack(pady=10)
        tk.Button(self, text="Voltar", command=lambda: master.switch_frame(MenuClienteProdutos), bg="#B67C00").pack()
    def finalizar_compra(self):
        qtd_str = self.quant_entry.get().strip()
        nome_cliente = self.nome_entry.get().strip()
        forma_pag = self.pag_combo.get().strip()
        if not qtd_str or not nome_cliente or not forma_pag:
            messagebox.showerror("Erro", "Preencha todos os campos.")
            return
        try:
            qtd = int(qtd_str)
            if qtd <= 0:
                raise ValueError()
        except:
            messagebox.showerror("Erro", "Quantidade inválida.")
            return
        total = self.produto["preco"] * qtd
        vendas.append({
            "produto": self.produto,
            "quantidade": qtd,
            "usuario": nome_cliente,
            "vendedor": "Cliente direto",
            "pagamento": forma_pag,
            "total": total
        })
        nota_fiscal = (
            "========== NOTA FISCAL ==========\n\n"
            f"Cliente: {nome_cliente}\n"
            f"Produto: {self.produto['nome']}\n"
            f"Marca: {self.produto['marca']}\n"
            f"Forma de pagamento: {forma_pag}\n"
            f"Quantidade: {qtd}\n"
            f"Valor unitário: R$ {self.produto['preco']:.2f}\n"
            f"TOTAL: R$ {total:.2f}\n\n"
            "================================="
        )
        messagebox.showinfo("Compra Realizada", nota_fiscal)
        self.master.switch_frame(MenuClienteProdutos)

class MenuClientes(tk.Frame):
    def __init__(self, master):
        super().__init__(master, bg="#2E2E2E")
        tk.Label(self, text="Clientes Cadastrados", font=("Arial", 16),fg="white",bg="#2e2e2e").pack(pady=10)
        self.tree = ttk.Treeview(self, columns=("ID", "Nome", "CPF", "Email", "Telefone"), show="headings")
        for col in ("ID", "Nome", "CPF", "Email", "Telefone"):
            self.tree.heading(col, text=col)
            self.tree.column(col, width=110)
        self.tree.pack(fill="both", expand=True, padx=10)
        self.atualizar_lista()
        btn_frame = tk.Frame(self,bg="#2E2E2E")
        btn_frame.pack(pady=10)
        tk.Button(btn_frame, text="Adicionar Cliente", command=self.adicionar_cliente,fg="white",bg="#B67C00").pack(side="left", padx=5)
        tk.Button(btn_frame, text="Remover Cliente", command=self.remover_cliente,fg="white",bg="#B67C00").pack(side="left", padx=5)
        tk.Button(btn_frame, text="Voltar", command=lambda: master.switch_frame(MenuFuncionario),fg="white",bg="#B67C00").pack(side="left", padx=5)
    def atualizar_lista(self):
        self.tree.delete(*self.tree.get_children())
        for i in range(len(nomes)):
            self.tree.insert("", tk.END, values=(ids[i], nomes[i], cpfs[i], emails[i], telefones[i]))
    def adicionar_cliente(self):
        top = tk.Toplevel(self)
        top.title("Adicionar Cliente")
        top.configure(bg="#2e2e2e")
        campos = ["ID", "Nome", "CPF", "Email", "Telefone"]
        entradas = {}
        for i, campo in enumerate(campos):
            tk.Label(top, text=f"{campo}:", bg="#2E2E2E").grid(row=i, column=0, padx=5, pady=5)
            entrada = tk.Entry(top)
            entrada.grid(row=i, column=1, padx=5, pady=5)
            entradas[campo.lower()] = entrada
        def salvar():
            novo = {k: entradas[k].get().strip() for k in entradas}
            if any(v == "" for v in novo.values()):
                messagebox.showerror("Erro", "Preencha todos os campos.")
                return
            ids.append(novo["id"],bg="#2e2e2e")
            nomes.append(novo["nome"],bg="#2e2e2e")
            cpfs.append(novo["cpf"],bg="#2e2e2e")
            emails.append(novo["email"],bg="#2e2e2e")
            telefones.append(novo["telefone"],bg="#2e2e2e")
            self.atualizar_lista()
            top.destroy()
        tk.Button(top, text="Salvar", command=salvar,fg="white",bg="#B67C00").grid(row=len(campos), column=0, columnspan=2, pady=10)
    def remover_cliente(self):
        selecionado = self.tree.selection()
        if not selecionado:
            messagebox.showwarning("Aviso", "Selecione um cliente para remover.")
            return
        item = self.tree.item(selecionado)
        cliente_id = item["values"][0]
        if cliente_id in ids:
            idx = ids.index(cliente_id)
            for lst in [ids, nomes, cpfs, emails, telefones]:
                lst.pop(idx)
            self.atualizar_lista()
            messagebox.showinfo("Sucesso", "Cliente removido.")

class GerenciarProdutos(tk.Frame):
    def __init__(self, master):
        super().__init__(master, bg="#2E2E2E")
        tk.Label(self, text="Gerenciar Produtos", font=("Arial", 16),bg="#2e2e2e").pack(pady=10)
        self.tree = ttk.Treeview(self, columns=("ID", "Nome", "Marca", "Preço"), show="headings")
        for col in ("ID", "Nome", "Marca", "Preço"):
            self.tree.heading(col, text=col)
            self.tree.column(col, width=130)
        self.tree.pack(fill="both", expand=True, padx=10)
        self.atualizar_lista()
        btn_frame = tk.Frame(self, bg="#2E2E2E")
        btn_frame.pack(pady=10)
        tk.Button(btn_frame, text="Adicionar Produto", command=self.adicionar_produto,fg="white",bg="#B67C00").pack(side="left", padx=5)
        tk.Button(btn_frame, text="Remover Produto", command=self.remover_produto,fg="white",bg="#B67C00").pack(side="left", padx=5)
        tk.Button(btn_frame, text="Voltar", command=lambda: master.switch_frame(MenuFuncionario),fg="white",bg="#B67C00").pack(side="left", padx=5)
    def atualizar_lista(self):
        self.tree.delete(*self.tree.get_children())
        for cat, produtos in tprodutos.items():
            for p in produtos:
                self.tree.insert("", tk.END, values=(p["id"], p["nome"], p["marca"], f"{p['preco']:.2f}"))
    def adicionar_produto(self):
        top = tk.Toplevel(self)
        top.title("Adicionar Produto")
        top.configure(bg="#2e2e2e")
        tk.Label(top, text="ID (ex: B001):",bg="#2e2e2e").grid(row=0, column=0, padx=5, pady=5)
        id_entry = tk.Entry(top)
        id_entry.grid(row=0, column=1, padx=5, pady=5)
        tk.Label(top, text="Nome:",bg="#2e2e2e").grid(row=1, column=0, padx=5, pady=5)
        nome_entry = tk.Entry(top)
        nome_entry.grid(row=1, column=1, padx=5, pady=5)
        tk.Label(top, text="Marca:",bg="#2e2e2e").grid(row=2, column=0, padx=5, pady=5)
        marca_entry = tk.Entry(top)
        marca_entry.grid(row=2, column=1, padx=5, pady=5)
        tk.Label(top, text="Preço:",bg="#2e2e2e").grid(row=3, column=0, padx=5, pady=5)
        preco_entry = tk.Entry(top)
        preco_entry.grid(row=3, column=1, padx=5, pady=5)
        def salvar():
            pid = id_entry.get().strip().upper()
            nome = nome_entry.get().strip()
            marca = marca_entry.get().strip()
            preco_str = preco_entry.get().strip()
            if not (pid and nome and marca and preco_str):
                messagebox.showerror("Erro", "Preencha todos os campos")
                return
            letra = pid[0]
            if letra not in tprodutos:
                messagebox.showerror("Erro", "Categoria do produto inválida (primeira letra do ID)")
                return
            try:
                preco = float(preco_str)
            except:
                messagebox.showerror("Erro", "Preço inválido")
                return
            novo_produto = {"id": pid, "nome": nome, "marca": marca, "preco": preco}
            tprodutos[letra].append(novo_produto)
            self.atualizar_lista()
            top.destroy()
        tk.Button(top, text="Salvar", command=salvar,fg="white",bg="#B67C00").grid(row=4, column=0, columnspan=2, pady=10)
    def remover_produto(self):
        selecionado = self.tree.selection()
        if not selecionado:
            messagebox.showwarning("Aviso", "Selecione um produto para remover.")
            return
        item = self.tree.item(selecionado)
        pid = item["values"][0]
        letra = pid[0]
        if letra in tprodutos:
            for p in tprodutos[letra]:
                if p["id"] == pid:
                    tprodutos[letra].remove(p)
                    self.atualizar_lista()
                    messagebox.showinfo("Sucesso", f"Produto {pid} removido.")
                    return
        messagebox.showerror("Erro", "Produto não encontrado.")

class RegistrarVenda(tk.Frame):
    def __init__(self, master):
        super().__init__(master, bg="#2E2E2E")
        tk.Label(self, text="Registrar Venda", font=("Arial", 16),bg="#2e2e2e").pack(pady=10)
        tk.Label(self, text="Selecione o Cliente:",bg="#2e2e2e").pack()
        self.cliente_combo = ttk.Combobox(self, values=nomes, state="readonly")
        self.cliente_combo.pack(pady=5)
        tk.Label(self, text="Selecione o Produto:",bg="#2e2e2e").pack()
        self.produto_combo = ttk.Combobox(self, values=self.produtos_para_combo(), state="readonly", width=50)
        self.produto_combo.pack(pady=5)
        tk.Label(self, text="Quantidade:",bg="#2e2e2e").pack()
        self.qtd_entry = tk.Entry(self)
        self.qtd_entry.pack(pady=5)
        tk.Label(self, text="Forma de Pagamento:", bg="#2E2E2E").pack()
        self.pag_combo = ttk.Combobox(self, values=["Cartão de crédito", "Cartão de débito", "Dinheiro", "Pix"], state="readonly")
        self.pag_combo.pack(pady=5)
        tk.Button(self, text="Registrar Venda", command=self.registrar_venda,fg="white",bg="#B67C00").pack(pady=10)
        tk.Button(self, text="Voltar", command=lambda: master.switch_frame(MenuFuncionario),fg="white",bg="#B67C00").pack()
    def produtos_para_combo(self):
        lista = []
        for cat, produtos in tprodutos.items():
            for p in produtos:
                lista.append(f"{p['id']} - {p['nome']} ({p['marca']}) - R${p['preco']:.2f}")
        return lista
    def registrar_venda(self):
        cliente = self.cliente_combo.get()
        produto_str = self.produto_combo.get()
        qtd_str = self.qtd_entry.get()
        pagamento = self.pag_combo.get()
        if not cliente or not produto_str or not qtd_str or not pagamento:
            messagebox.showerror("Erro", "Preencha todos os campos")
            return
        try:
            qtd = int(qtd_str)
            if qtd <= 0:
                raise ValueError()
        except:
            messagebox.showerror("Erro", "Quantidade inválida")
            return
        pid = produto_str.split(" - ")[0]
        produto = None
        for cat, produtos in tprodutos.items():
            for p in produtos:
                if p["id"] == pid:
                    produto = p
                    break
            if produto:
                break
        if not produto:
            messagebox.showerror("Erro", "Produto não encontrado")
            return
        total = produto["preco"] * qtd
        vendas.append({
            "produto": produto,
            "quantidade": qtd,
            "usuario": cliente,
            "vendedor": "Funcionário",
            "pagamento": pagamento,
            "total": total
        })
        messagebox.showinfo("Sucesso", f"Venda registrada!\nCliente: {cliente}\nProduto: {produto['nome']}\nQuantidade: {qtd}\nTotal: R${total:.2f}")
        self.master.switch_frame(MenuFuncionario)

class MenuFuncionarios(tk.Frame):
    def __init__(self, master):
        super().__init__(master, bg="#2E2E2E")
        tk.Label(self, text="Funcionários Cadastrados", font=("Arial", 16),bg="#2e2e2e").pack(pady=10)
        self.tree = ttk.Treeview(self, columns=("ID", "Nome", "CPF", "Email", "Telefone", "Salario"), show="headings")
        for col in ("ID", "Nome", "CPF", "Email", "Telefone", "Salario"):
            self.tree.heading(col, text=col)
            self.tree.column(col, width=110)
        self.tree.pack(fill="both", expand=True, padx=10)
        self.atualizar_listas()
        btn_frame = tk.Frame(self,bg="#2e2e2e")
        btn_frame.pack(pady=10)
        tk.Button(btn_frame, text="Adicionar Funcionário", command=self.adicionar_funcionario,fg="white",bg="#B67C00").pack(side="left", padx=5)
        tk.Button(btn_frame, text="Remover Funcionário", command=self.remover_funcionario,fg="white",bg="#B67C00").pack(side="left", padx=5)
        tk.Button(btn_frame, text="Voltar", command=lambda: master.switch_frame(MenuFuncionario),fg="white",bg="#B67C00").pack(side="left", padx=5)
    def atualizar_listas(self):
        self.tree.delete(*self.tree.get_children())
        for i in range(len(nomes1)):
            self.tree.insert("", tk.END, values=(ids1[i], nomes1[i], cpfs1[i], email1[i], telefones1[i], salario[i]))
    def adicionar_funcionario(self):
        top = tk.Toplevel(self)
        top.title("Adicionar Funcionario")
        top.configure(bg="#2e2e2e")
        campos = ["ID", "Nome", "CPF", "Email", "Telefone","Salario"]
        entradas = {}
        for i, campo in enumerate(campos):
            tk.Label(top, text=f"{campo}:", bg="#2E2E2E").grid(row=i, column=0, padx=5, pady=5)
            entrada = tk.Entry(top)
            entrada.grid(row=i, column=1, padx=5, pady=5)
            entradas[campo.lower()] = entrada
        def salvar():
            novo = {k: entradas[k].get().strip() for k in entradas}
            if any(v == "" for v in novo.values()):
                messagebox.showerror("Erro", "Preencha todos os campos.")
                return
            ids1.append(novo["id"] )
            nomes1.append(novo["nome"])
            cpfs1.append(novo["cpf"])
            email1.append(novo["email"])
            telefones1.append(novo["telefone"])
            salario.append(novo["salario"])
            self.atualizar_listas()
            top.destroy()
        tk.Button(top, text="Salvar", command=salvar,fg="white",bg="#B67C00").grid(row=len(campos), column=0, columnspan=2, pady=10)
    def remover_funcionario(self):
        selecionado = self.tree.selection()
        if not selecionado:
            messagebox.showwarning("Aviso", "Selecione um funcionário para remover.")
            return
        item = self.tree.item(selecionado)
        funcionario_id = item["values"][0]
        if funcionario_id in ids1:
            idx = ids1.index(funcionario_id)
            for lst in [ids1, nomes1, cpfs1, email1, telefones1,salario]:
                lst.pop(idx)
            self.atualizar_listas()
            messagebox.showinfo("Sucesso", "Funcionário removido.")

class RelatorioVendas(tk.Frame):
    def __init__(self, master):
        super().__init__(master, bg="#2E2E2E")
        tk.Label(self, text="Relatório de Vendas", font=("Arial", 16), bg="#2E2E2E").pack(pady=10)
        self.tree = ttk.Treeview(self, columns=("Cliente", "Produto", "Qtd", "Vendedor", "Pagamento", "Total"), show="headings")
        for col in ("Cliente", "Produto", "Qtd", "Vendedor", "Pagamento", "Total"):
            self.tree.heading(col, text=col)
            self.tree.column(col, width=100)
        self.tree.pack(fill="both", expand=True, padx=10)
        self.total_label = tk.Label(self, text="Total da loja: R$ 0.00", font=("Arial", 12),  bg="#2E2E2E")
        self.total_label.pack(pady=5)
        self.atualizar_lista()
        tk.Button(self, text="Voltar", command=lambda: master.switch_frame(MenuFuncionario), fg="white", bg="#B67C00").pack(pady=10)
    def atualizar_lista(self):
        self.tree.delete(*self.tree.get_children())
        total_loja = 0
        for v in vendas:
            total_loja += v['total']
            self.tree.insert("", tk.END, values=(
                v["usuario"],
                v["produto"]["nome"],
                v["quantidade"],
                v["vendedor"],
                v["pagamento"],
                f"R${v['total']:.2f}"
            )
        self.total_label.config(text=f"Total da loja: R$ {total_loja:.2f}")

if __name__ == "__main__":
    app = LojaApp()
    app.mainloop()
