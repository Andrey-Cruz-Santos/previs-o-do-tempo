import tkinter as tk  # Importa o Tkinter

root = tk.Tk()  # Cria a janela principal
root.title("Título da Janela")  # Define o título

root.mainloop()  # Mantém a janela aberta
import tkinter as tk

# Função chamada quando o botão é clicado
def greet():
    name = entry.get()  # Obtém o texto do campo de entrada
    label.config(text=f"Olá, {name}!")  # Atualiza o texto do label

# Passo 1: Criar a janela principal
root = tk.Tk()  # Cria a janela principal
root.title("Aplicação de Saudação")  # Define o título da janela

# Passo 2: Criar um label
label = tk.Label(root, text="Digite seu nome:")  # Cria um label
label.pack(pady=10)  # Adiciona o label à janela e espaçamento vertical

# Passo 3: Criar um campo de entrada
entry = tk.Entry(root)  # Cria um campo de entrada
entry.pack(pady=5)  # Adiciona o campo à janela e espaçamento vertical

# Passo 4: Criar um botão
button = tk.Button(root, text="Saudar", command=greet)  # Cria um botão que chama a função greet
button.pack(pady=20)  # Adiciona o botão à janela e espaçamento vertical

# Passo 5: Iniciar o loop principal
root.mainloop()  # Mantém a janela aberta

import requests

# Função para pegar a previsão do tempo
def get_weather(city):
    api_key = "SUA_API_KEY"  # Insira sua chave de API aqui
    base_url = "http://https://www.apac.pe.gov.br/previsoes-do-tempo"
    
    # URL com os parâmetros da cidade e chave
    complete_url = f"{base_url}?q={city}&appid={api_key}&units=metric&lang=pt_br"
    
    try:
        response = requests.get(complete_url)

        # Verifica se a resposta é válida
        if response.status_code == 200:
            data = response.json()
            # Extraindo dados principais
            main = data['main']
            weather = data['weather'][0]
            wind = data['wind']

            print(f"Previsão do tempo em {city.capitalize()}:")
            print(f"Temperatura: {main['temp']}°C")
            print(f"Clima: {weather['description'].capitalize()}")
            print(f"Umidade: {main['humidity']}%")
            print(f"Velocidade do Vento: {wind['speed']} m/s")
        else:
            print(f"Erro ao obter dados para {city}. Verifique o nome da cidade.")
    except Exception as e:
        print(f"Ocorreu um erro ao tentar se conectar à API: {e}")

# Exemplo de uso
if __name__ == "__main__":
    cidade = input("Digite o nome da cidade: ")
    get_weather(cidade)
