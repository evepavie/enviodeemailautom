import pyautogui
import pyperclip
import time 
pyautogui.PAUSE=1
pyautogui.hotkey("ctrl","t") #abrir nova aba
pyperclip.copy("https://drive.google.com/drive/folders/149xknr9JvrlEnhNWO49zPcw0PW5icxga?usp=sharing") #link do drive
pyautogui.hotkey("ctrl", "v")
pyautogui.press("enter")
time.sleep(5)
#passo2-navegar no sistema (até a pasta exportar)
pyautogui.click(x=309, y=261, clicks=2)#clicar na pasta exportar

#passo3-fazer download da base de vendas 
pyautogui.click(x=369, y=251)#clicar na pasta vendas
pyautogui.click(x=1161, y=154)#clicar em tres pontos
pyautogui.click(x=952, y=560)#clicar em download
time.sleep(8)#esperar download

import pandas as pd

#passo4-importar a base de vendas para Python
tabela = pd.read_excel(r'C:\Users\user\Downloads\Aula 1-20220110T230432Z-001\Aula 1\Exportar\Vendas - Dez.xlsx')
display(tabela)#é usado para poder visualizar a tabela

#passo5-calcular o faturamento e quantidade de produtos vendidos 
faturamento = tabela["Valor Final"].sum()#somando todos os valores do valor final
qt_de_produto = tabela["Quantidade"].sum()#somando o total de quantidade
display(faturamento)
display(qt_de_produt

#passo6-enviar o email para diretoria
pyautogui.hotkey("ctrl", "t")#abrir aba nova
pyperclip.copy(r"https://mail.google.com/mail/u/0/#inbox")#copiar link gmail
pyautogui.hotkey("ctrl", "v")#colar link gmail
pyautogui.press("enter")#confirmar
time.sleep(5)
pyautogui.click(x=91, y=175)#localizaçao para clicar no escrever
pyautogui.write("pavieeve@gmail.com")#email destinatario
time.sleep(6)
pyautogui.press("tab")#selecionar o email
pyautogui.press("tab")#vai para o campo de baixo(assunto)
pyautogui.write("intensivao aula 1")#escrever o assunto
pyautogui.press("tab")#vai para escrever email
texto = f""" Prezada diretoria,
De acordo com os dados informados pode se ter o resultado a seguir   faturamento é  {faturamento:,.2f}, e a quantidade de produtos total é {qt_de_produto}"""#aspas triplas é para poder colocar o texto da forma que preferir, sempre colocar o f antes 
pyperclip.copy(texto)#copiar o texto
pyautogui.hotkey("ctrl", "v")
pyautogui.hotkey("ctrl", "enter")

time.sleep(5)
pyautogui.position()
