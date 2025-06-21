import http.server
import socketserver

PORT = 8000
REDIRECT_URL = "https://github.com/chizrueportfolio/portfolio.git"

class RedirectHandler(http.server.SimpleHTTPRequestHandler):
    def do_GET(self):
        self.send_response(302)
        self.send_header('Location', REDIRECT_URL)
        self.end_headers()

with socketserver.TCPServer(("", PORT), RedirectHandler) as httpd:
    print(f"Serving redirect on port {PORT}...")
    httpd.serve_forever()
