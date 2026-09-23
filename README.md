# actividad5_phyton_chatbot
hola este es un poco de la explicación de como fue este proceso de Python y el chat Bot espero les guste.
PAGINA WEB:Primero iniciamos pasando la pagina de HTML a Python ,  aca observamos conmo era la pagina en html y como es haora en python.
<img width="819" height="603" alt="image" src="https://github.com/user-attachments/assets/93c2a0dd-1d04-4009-87e7-69c782e62c57" />
<img width="832" height="544" alt="image" src="https://github.com/user-attachments/assets/4178a477-162f-4246-b470-fd57c5708e8a" />
<img width="1290" height="582" alt="image" src="https://github.com/user-attachments/assets/d86d0935-ee20-413b-875b-6cd205186436" />
<img width="1164" height="610" alt="image" src="https://github.com/user-attachments/assets/e2ce00b3-8c53-462b-983a-5ecc261af79e" />

De igual manera acá dejo el link de la pagina web
[paginaweb.py](https://github.com/user-attachments/files/32570127/paginaweb.py)

Ahora daré la explicación de el chat bot:
Utilice ollama: ollama me permitió descargar el chat Bot de manera local sin necesidad de un apky , primero instalamos ollama y buscamos la parte de el chat bot que queremos descargar. 
En mi caso use la versión  qwen2.5:0.5b , como la instale?

Primero ingrese a el símbolo de sistema , hay empecé a dar unos comandos para poder realizar la descarga. en este orden:
<img width="1133" height="209" alt="image" src="https://github.com/user-attachments/assets/acd626af-a750-4f83-b37b-5bfcef09a6a1" />

"Jugando con este chat Bot me di cuenta que usaba parámetros de Python para generar las respuestas por ejemplo cuando le pregunte cuanto es 2 + 2 me lanzo a la consola una parte de 
Python esta idealizando tu respuesta ", entonces hay entere en curiosidad y quise saber como es el código del chat Bot desde Python y como se puede personalisar.
el CODIGO QUE CONSEFGUI DE ESTE CHAT  BOT EN PYTHON FUE ESTE:

#explicacionn ,codigo de chat gpt version qwen2.5:0.5b en pyhon ,teniendo en cuenta parametros del codigo poriginal


import ollama

# 1. Definir el modelo que vas a usar
MODEL_NAME = 'qwen2.5:0.5b'

# 2. Inicializar el historial del chat con instrucciones estrictas
messages = [
    {
        'role': 'system', 
        'content': 'Eres un asistente inteligente y amable. Responde a lo que te pida el usuario de forma pensante y especifica.'
    }
]

print("🤖 Chat personalizado iniciado. Escribe 'salir' para terminar.\n")

while True:
    # 3. Leer la entrada del usuario
    user_input = input("Tú: ")
    if user_input.lower() in ['salir', 'exit', 'quit']:
        print("¡Adiós! masamorra feliz ¡que tengas un bonito dia!")
        break
        
    if not user_input.strip():
        continue

    # 4. Añadir el mensaje del usuario al historial
    messages.append({'role': 'user', 'content': user_input})

    print("Qwen: ", end='', flush=True)

    try:
        # 5. Enviar la conversación a Ollama usando streaming
        response_stream = ollama.chat(
            model=MODEL_NAME,
            messages=messages,
            stream=True
        )

        # 6. Imprimir la respuesta normal del modelo
        full_response = ""
        for chunk in response_stream:
            content = chunk['message']['content']
            print(content, end='', flush=True)
            full_response += content
            
        # 7. Forzar el remate personalizado al final de la respuesta para que sea una personalizacion mas interactiva por ejemplo yo escogi masamorra feliz al final de cada texto
        remate = " masamorra feliz"
        print(remate) # Esto lo imprime inmediatamente en la pantalla del usuario
        
        # Guardamos la respuesta completa (incluyendo el remate) en el historial 
        # para que el modelo recuerde que ya lo dijo en el próximo turno
        full_response += remate
        messages.append({'role': 'assistant', 'content': full_response})

    except Exception as e:
        print(f"\n❌ Error al conectar con Ollama: {e}")
        break
        remate = "el dios miguel esta tratando de buscar el problema , espera un poco;)"
        print(remate)

Lo mas interesante es la cantidad de oportunidades que nos da de personalización este código por ejemplo los REMATE que son para agregar una respuesta personalizada después de cada respuesta que nos da el chat Bot 
en mi caso yo coloque masamorra feliz al final de cada respuesta y cuando pasaba ubn error con el chat bot coloque el dios miguel esta intentando solucionar el problema.

 EN CONCLUCION ESTO FUE UN PIOCO EL PROCESO DE LA INSTAKLACION DEL CHATBO Y COMO ES EL CODIGO DESDE PYTHON AGREGANDO LA PARTE DE DE LA PAGINA WEB
