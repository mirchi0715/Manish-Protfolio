from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('index.html')

@app.route('/about')
def about():
    return render_template('about.html')

@app.route('/projects')
def projects():
    return render_template('projects.html')

@app.route('/contact', methods=['GET', 'POST'])
def contact():
    if request.method == 'POST':
        name = request.form['name']
        email = request.form['email']
        message = request.form['message']
        # Process form submission (e.g., store data, send email)
    return render_template('contact.html')

if __name__ == '__main__':
    app.run(debug=True)

# Frontend Files:

# templates/index.html
"""
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home - Portfolio</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='css/style.css') }}">
</head>
<body>
    <header>
        <h1>Welcome to My Portfolio</h1>
        <nav>
            <a href="/">Home</a>
            <a href="/about">About</a>
            <a href="/projects">Projects</a>
            <a href="/contact">Contact</a>
        </nav>
    </header>
    <section>
        <p>Hello! I am [Your Name], a passionate developer.</p>
    </section>
</body>
</html>
"""

# templates/about.html
"""
<!DOCTYPE html>
<html lang="en">
<head>
    <title>About Me</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='css/style.css') }}">
</head>
<body>
    <header>
        <h1>About Me</h1>
        <nav>
            <a href="/">Home</a>
            <a href="/about">About</a>
            <a href="/projects">Projects</a>
            <a href="/contact">Contact</a>
        </nav>
    </header>
    <section>
        <p>I am a web developer with experience in Flask, HTML, CSS, and JavaScript.</p>
    </section>
</body>
</html>
"""

# static/css/style.css
"""
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}
header {
    background: #333;
    color: white;
    padding: 1rem;
    text-align: center;
}
nav a {
    margin: 0 15px;
    color: white;
    text-decoration: none;
}
section {
    padding: 20px;
    text-align: center;
}
"""
