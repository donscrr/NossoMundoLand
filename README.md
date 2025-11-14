# NossoMundoLand
Sitio web de Andrea 
# Vamos criar um arquivo zip com HTML, CSS e um exemplo de imagem para o site.
import zipfile
import os

# Criar pasta temporária para os arquivos
os.makedirs("/mnt/data/sitio_andrea", exist_ok=True)

# Criar arquivo HTML
html_content = """
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sitio de Andrea</title>
<link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Bienvenida al sitio de Andrea</h1>
    </header>
    <section>
        <p>¡Este es un sitio hecho con cariño! 💖</p>
        <img src="andrea.jpg" alt="Andrea">
    </section>
    <footer>
        <p>Creado por <strong>donscrr</strong></p>
    </footer>
</body>
</html>
"""

with open("/mnt/data/sitio_andrea/index.html", "w") as f:
    f.write(html_content)

# Criar arquivo CSS
css_content = """
body {
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: #fff0f5;
    color: #333;
}
header {
    background-color: #ffb6c1;
    padding: 20px;
}
section img {
    max-width: 80%;
    height: auto;
    border-radius: 10px;
    margin-top: 20px;
}
footer {
    margin-top: 30px;
    font-size: 0.9em;
    color: #555;
}
"""

with open("/mnt/data/sitio_andrea/style.css", "w") as f:
    f.write(css_content)

# Criar um arquivo de imagem de exemplo (placeholder)
from PIL import Image, ImageDraw

img = Image.new('RGB', (600, 400), color=(255, 182, 193))
d = ImageDraw.Draw(img)
d.text((150,180), "Foto de Andrea", fill=(0,0,0))
img.save("/mnt/data/sitio_andrea/andrea.jpg")

# Criar arquivo ZIP
zip_filename = "/mnt/data/sitio_andrea.zip"
with zipfile.ZipFile(zip_filename, 'w') as zipf:
    for root, dirs, files in os.walk("/mnt/data/sitio_andrea"):
        for file in files:
            zipf.write(os.path.join(root, file), arcname=file)

zip_filename
