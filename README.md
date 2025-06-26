from zipfile import ZipFile
import os

# Recreate the site directory and content since the state was reset
site_dir = "/mnt/data/restore_hope_site"
os.makedirs(site_dir, exist_ok=True)

# Define HTML and CSS content again
pages = {
    "index.html": "<!DOCTYPE html><html lang='en'><head><meta charset='UTF-8'><title>Restore Hope Foundation</title><link rel='stylesheet' href='style.css'></head><body><header><h1>Restore Hope Foundation</h1><p class='tagline'>Restoring hope one story at a time</p><nav><a href='index.html'>Home</a><a href='about.html'>About</a><a href='books.html'>Books</a><a href='games.html'>Games</a><a href='courses.html'>Courses</a><a href='donate.html'>Donate</a><a href='contact.html'>Contact</a></nav></header><main><section><h2>Welcome</h2><p>Explore our stories, games, and courses to bring hope and healing to the world.</p></section></main><footer><p>&copy; 2025 Restore Hope Foundation</p></footer></body></html>",
    "about.html": "<!DOCTYPE html><html lang='en'><head><meta charset='UTF-8'><title>About</title><link rel='stylesheet' href='style.css'></head><body><header><h1>About Us</h1><nav><a href='index.html'>Home</a><a href='about.html'>About</a><a href='books.html'>Books</a><a href='games.html'>Games</a><a href='courses.html'>Courses</a><a href='donate.html'>Donate</a><a href='contact.html'>Contact</a></nav></header><main><section><h2>Our Mission</h2><p>We believe stories can heal. Through books, games, and education, we help people reclaim hope.</p></section></main><footer><p>&copy; 2025 Restore Hope Foundation</p></footer></body></html>",
    "books.html": "<!DOCTYPE html><html lang='en'><head><meta charset='UTF-8'><title>Books</title><link rel='stylesheet' href='style.css'></head><body><header><h1>Books</h1><nav><a href='index.html'>Home</a><a href='about.html'>About</a><a href='books.html'>Books</a><a href='games.html'>Games</a><a href='courses.html'>Courses</a><a href='donate.html'>Donate</a><a href='contact.html'>Contact</a></nav></header><main><section><h2>Our Stories</h2><p>Discover books that inspire healing and spark hope, including Rowan the Amazing Letter Superhero and more.</p></section></main><footer><p>&copy; 2025 Restore Hope Foundation</p></footer></body></html>",
    "games.html": "<!DOCTYPE html><html lang='en'><head><meta charset='UTF-8'><title>Games</title><link rel='stylesheet' href='style.css'></head><body><header><h1>Games</h1><nav><a href='index.html'>Home</a><a href='about.html'>About</a><a href='books.html'>Books</a><a href='games.html'>Games</a><a href='courses.html'>Courses</a><a href='donate.html'>Donate</a><a href='contact.html'>Contact</a></nav></header><main><section><h2>Princesses of Hope</h2><p>A magical hidden-object game where players restore hope to towns across the kingdom.</p></section></main><footer><p>&copy; 2025 Restore Hope Foundation</p></footer></body></html>",
    "courses.html": "<!DOCTYPE html><html lang='en'><head><meta charset='UTF-8'><title>Courses</title><link rel='stylesheet' href='style.css'></head><body><header><h1>Courses</h1><nav><a href='index.html'>Home</a><a href='about.html'>About</a><a href='books.html'>Books</a><a href='games.html'>Games</a><a href='courses.html'>Courses</a><a href='donate.html'>Donate</a><a href='contact.html'>Contact</a></nav></header><main><section><h2>Learn With Us</h2><p>Explore empowering courses like our astrology course on Leo and other personal growth journeys.</p></section></main><footer><p>&copy; 2025 Restore Hope Foundation</p></footer></body></html>",
    "donate.html": "<!DOCTYPE html><html lang='en'><head><meta charset='UTF-8'><title>Donate</title><link rel='stylesheet' href='style.css'></head><body><header><h1>Donate</h1><nav><a href='index.html'>Home</a><a href='about.html'>About</a><a href='books.html'>Books</a><a href='games.html'>Games</a><a href='courses.html'>Courses</a><a href='donate.html'>Donate</a><a href='contact.html'>Contact</a></nav></header><main><section><h2>Support Our Mission</h2><p>Your donation helps us bring hope to others through storytelling, education, and interactive healing.</p></section></main><footer><p>&copy; 2025 Restore Hope Foundation</p></footer></body></html>",
    "contact.html": "<!DOCTYPE html><html lang='en'><head><meta charset='UTF-8'><title>Contact</title><link rel='stylesheet' href='style.css'></head><body><header><h1>Contact Us</h1><nav><a href='index.html'>Home</a><a href='about.html'>About</a><a href='books.html'>Books</a><a href='games.html'>Games</a><a href='courses.html'>Courses</a><a href='donate.html'>Donate</a><a href='contact.html'>Contact</a></nav></header><main><section><h2>We’d Love to Hear From You</h2><p>Email: info@restorehopefoundation.com</p></section></main><footer><p>&copy; 2025 Restore Hope Foundation</p></footer></body></html>",
    "style.css": "body {font-family: 'Arial', sans-serif;background-color: #fdf6f0;color: #333;margin: 0;padding: 0;}header {background-color: #f4c2c2;padding: 1em;text-align: center;}nav a {margin: 0 15px;text-decoration: none;color: #333;font-weight: bold;}.tagline {font-style: italic;font-size: 1.2em;margin-top: -10px;}main {padding: 20px;}footer {background-color: #f4c2c2;text-align: center;padding: 1em;position: fixed;bottom: 0;width: 100%;}"
}

# Write the files to the directory
for filename, content in pages.items():
    with open(os.path.join(site_dir, filename), 'w') as f:
        f.write(content)

# Create the zip file
zip_path = "/mnt/data/restore_hope_site.zip"
with ZipFile(zip_path, 'w') as zipf:
    for filename in pages:
        zipf.write(os.path.join(site_dir, filename), arcname=filename)

zip_path
