# ChatGPT con Mistral 7B
Notebook de cómo usar el modelo Mistral 7B 

# Inicio rápido
Paso 1)
Crea un Notebook con Python 3.8 o superior

Paso 2)
Desde consola installa las librerias requeridas usando:
`pip install gpt4all`

Paso 3)
Descarga el modelo Mistral 7b desde:
https://huggingface.co/TheBloke/Mistral-7B-Instruct-v0.1-GGUF/blob/main/mistral-7b-instruct-v0.1.Q4_0.gguf

Podras descargar otros modelos similares desde:
https://huggingface.co/TheBloke/Mistral-7B-Instruct-v0.1-GGUF

# Ejemplo de GPT4All
Basico:

```python
from gpt4all import GPT4All
model = GPT4All("mistral-7b-instruct-v0.1.Q4_0.gguf")
output = model.generate("The capital of France is ", max_tokens=3)
print(output)
```

Modo Chat:

```python
model = GPT4All(model_name='mistral-7b-instruct-v0.1.Q4_0.gguf')
with model.chat_session():
    response1 = model.generate(prompt='hello', temp=0)
    response2 = model.generate(prompt='write me a short poem', temp=0)
    response3 = model.generate(prompt='thank you', temp=0)
    print(model.current_chat_session)
```

Modo Streaming (Similar a como aparece el texto en ChatGPT):

```python
from gpt4all import GPT4All
model = GPT4All("mistral-7b-instruct-v0.1.Q4_0.gguf")
tokens = []
for token in model.generate("The capital of France is", max_tokens=20, streaming=True):
    tokens.append(token)
print(tokens)
```

Modo de gestion de plantillas:

En éste ejemplo lo que se hace es indicar como se le pasaran parametros al modelo para que responda en modo CHAT (Usuario / Assistente)

```python
from gpt4all import GPT4All
model = GPT4All('wizardlm-13b-v1.2.Q4_0.gguf')
system_template = 'A chat between a curious user and an artificial intelligence assistant.'
# many models use triple hash '###' for keywords, Vicunas are simpler:
prompt_template = 'USER: {0}\nASSISTANT: '
with model.chat_session(system_template, prompt_template):
    response1 = model.generate('why is the grass green?')
    print(response1)
    print()
    response2 = model.generate('why is the sky blue?')
    print(response2)
```


Para conocer mas solo ve a:

https://docs.gpt4all.io/
