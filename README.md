# Importar
from flask import Flask, render_template, request, send_from_directory


app = Flask(__name__)

# Resultados del formulario
@app.route('/', methods=['GET','POST'])
def index():
    if request.method == 'POST':
        # obtener la imagen seleccionada
        selected_image = request.form.get('image-selector')
        textTop = request.form.get('textTop', '')
        textBottom = request.form.get('textBottom', '')
        text_color = request.form.get('color-selector', 'white')
        textTop_y = request.form.get('textTop_y', '10%')
        textBottom_y = request.form.get('textBottom_y', '90%')

        

        # Assignment #3. Receiving the text's positioning
       

        # Asignación #3. Recepción del posicionamiento del texto
        

        return render_template('index.html', 
                               # Visualización de la imagen seleccionada
                               selected_image=selected_image,
                               textTop=textTop, 
                               textBottom=textBottom,
                               text_color=text_color,
                               textTop_y=textTop_y,
                               textBottom_y=textBottom_y 
                            
                               # Asignación #2. Visualización del texto
                               

                               #  Asignación #3. Visualización del color
                               
                               
                               # Asignación #3. Visualización de la posición del texto
                               

                               )
    else:
        # Mostrar la primera imagen por defecto
        return render_template('index.html', selected_image='logo.svg')


@app.route('/static/img/<path:path>')
def serve_images(path):
    return send_from_directory('static/img', path)

app.run(debug=True)
