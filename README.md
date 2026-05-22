import streamlit as st
import nltk
from nltk.tokenize import word_tokenize
from collections import Counter

# Garantindo os recursos
try:
    nltk.data.find('tokenizers/punkt_tab')
except LookupError:
    nltk.download('punkt')
    nltk.download('punkt_tab')

# 1. Texto de exemplo (simulando múltiplas mensagens)
mensagem_cliente = "A empresa recebe centenas de mensagens. As mensagens de clientes chegam todos os dias."

# 2. Tokenização
tokens = word_tokenize(mensagem_cliente, language='portuguese')

# 3. Filtragem: Mantém apenas o que for palavra (remove pontos e exclamações) e padroniza em minúsculas
palavras = [token.lower() for token in tokens if token.isalpha()]

# 4. Contagem de frequência
frequencia = Counter(palavras)

print("Tokens limpos (sem pontuação):")
print(palavras)

print("\nFrequência das palavras:")
print(dict(frequencia))
