Cloud-Native Portfolio Website

Dieses Repository enthält den Quellcode und die Infrastruktur-Konfiguration für meine persönliche Portfolio-Webseite. Das Projekt dient als Live-Demonstration moderner DevOps-Praktiken, Cloud-Infrastruktur-Management und Automatisierung.

Live Demo: https://mahdi-sharbaf.me

Tech-Stack & Architektur

Dieses Projekt wurde entwickelt, um High-Performance, Sicherheit und Automatisierung zu gewährleisten.

Cloud Provider: Microsoft Azure (Hosting auf einer Ubuntu Virtual Machine, B-Series)

Containerisierung: Docker (Isolierung der Anwendung in Containern)

Webserver: Nginx (Verwendung von Nginx Alpine für minimalen Footprint)

CI/CD: GitHub Actions (Vollautomatisierte Deployment-Pipeline)

Sicherheit & CDN: Cloudflare (SSL/TLS Verschlüsselung, DDoS-Schutz & DNS Management)

Betriebssystem: Linux (Ubuntu Server 24.04 LTS mit Server Hardening)

CI/CD Pipeline (Automatisierung)

Der Deployment-Prozess ist vollständig durch GitHub Actions automatisiert. Es ist kein manueller Eingriff auf dem Server erforderlich.

Workflow-Schritte (deploy.yml):

Trigger: Push auf den main Branch.

SSH Connection: Sichere Verbindung zur Azure VM via SSH-Keys.

Git Sync: Abrufen des neuesten Codes (git fetch & git reset).

Docker Build: Erstellung des neuen Docker-Images (ohne Cache).

Deployment: Neustart des Containers mit Zero-Downtime Strategie.

Lokale Installation

Um das Projekt lokal zu testen, benötigen Sie Docker installiert.

Repository klonen:

git clone [https://github.com/mahdisharbaf/my-resume-site.git](https://github.com/mahdisharbaf/my-resume-site.git)
cd my-resume-site


Docker Image bauen:

docker build -t my-portfolio .


Container starten (auf Port 8080):

docker run -d -p 8080:80 --name my-portfolio-container my-portfolio


Die Seite ist nun unter http://localhost:8080 erreichbar.

Sicherheitsmaßnahmen

Firewall (UFW): Nur Ports 22 (SSH), 80 (HTTP) und 443 (HTTPS) sind geöffnet.

SSH Hardening: Passwort-Login deaktiviert, Zugriff nur via Public-Key-Authentifizierung.

Cloudflare Proxy: Die echte IP-Adresse des Servers ist maskiert (Proxied DNS), um direkte Angriffe zu verhindern.

Minimal Base Image: Verwendung von nginx:alpine zur Reduzierung der Angriffsfläche.

Kontakt

Mahdi Sharbaf Movassaghpour
Cloud & DevOps Engineer | M.Eng Student

LinkedIn: https://linkedin.com/in/mahdi-sharbaf-movassaghpour

Website: https://mahdi-sharbaf.me