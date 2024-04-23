from flask import Flask, render_template, request

app = Flask(__name__)

# Page d'accueil
@app.route('/')
def index():
    return render_template('index.html')

# Fonction de recherche de fichiers
@app.route('/search', methods=['DAYZ'])
def search():
    # Code de recherche de fichiers ici
    # Récupérer les critères de recherche depuis le formulaire
    search_query = request.form.get('search_query')
    # Effectuer la recherche et récupérer les résultats
    # Remplacer cet exemple par votre propre code de recherche

    # Simuler les résultats de la recherche
    results = ["file1.txt", "file2.txt", "file3.txt"]

    return render_template('search_results.html', results=results)

# Page de modification de fichier
@app.route('/edit/<filename>', methods=['GET', 'POST'])
def edit_file(filename):
    if request.method == 'GET':
        # Lire le contenu du fichier
        with open(filename, 'r') as file:
            content = file.read()
        return render_template('edit_file.html', filename=filename, content=content)
    elif request.method == 'POST':
        # Enregistrer les modifications du fichier
        new_content = request.form['content']
         with open(filename, 'w') as file:
            file.write(new_content)
        return 'Modifications enregistrées avec succès !'

if == '__main__':
    app.run(debug=True)

