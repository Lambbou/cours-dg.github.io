# Portail Pédagogique — cours-dg.github.io

Site statique de ressources pédagogiques, compléments de cours et quiz d'auto-évaluation formative pour les étudiants de l'**ENSSAT** (Université de Rennes).

🌐 **Accès en ligne :** [https://cours-dg.github.io/](https://cours-dg.github.io/)

---

## 📌 Présentation

Ce site sert de point de convergence et de hub d'accès pour les étudiants afin de :
- Consulter des ressources complémentaires aux séances de cours magistraux et travaux dirigés.
- S'entraîner en autonomie grâce à des **quiz interactifs auto-corrigés**, fournissant des explications pas-à-pas immédiates.
- Préparer les évaluations formatives et réviser les concepts clés à leur propre rythme.

Le site est entièrement statique (HTML5 / CSS3 / JavaScript vanilla), sans base de données ni système de build, garantissant une rapidité d'affichage optimale, une pérennité maximale et un déploiement instantané via **GitHub Pages**.

---

## 📁 Architecture du Répertoire

Le site repose sur une organisation modulaire par matière :

```text
cours-dg.github.io/
├── index.html                  # 🏠 Page d'accueil principale du portail
├── README.md                   # 📖 Documentation et guide d'administration
├── doo/                        # 📦 Dossier du cours "Développement Objet I" (DOO)
│   ├── index.html              # Page d'atterrissage et synthèse du module DOO
│   ├── doo-quiz-cm-1.html      # Quiz 1 : Fondements POO & Associations UML (12 questions)
│   └── doo-quiz-cm-2.html      # Quiz 2 : Relations Avancées & Diagrammes d'États (12 questions)
└── [nouveau-cours]/            # 📂 Emplacement pour futurs cours (ex: algo/, web/, etc.)
```

---

## 🛠️ Guide de Gestion & Ajout de Contenus

### 1. Ajouter un nouveau quiz à un cours existant (ex: DOO)

1. **Dupliquer** l'un des quiz existants pour conserver la mise en page et le moteur interactif :
   ```bash
   cp doo/doo-quiz-cm-2.html doo/doo-quiz-cm-3.html
   ```

2. **Éditer les métadonnées** dans `doo/doo-quiz-cm-3.html` :
   - Modifier la balise `<title>` et le titre `<h1>`.
   - Mettre à jour le badge et le sous-titre descriptif.

3. **Renseigner les questions** dans le tableau JavaScript `const questions = [...]` en bas du fichier :
   ```javascript
   const questions = [
     {
       title: "1. Titre de la notion",
       text: "Énoncé précis de la question posée à l'étudiant ?",
       choices: [
         { text: "Proposition fausse 1", correct: false },
         { text: "Proposition correcte", correct: true },
         { text: "Proposition fausse 2", correct: false }
       ],
       feedback: "Explication détaillée de la bonne réponse affichée immédiatement après validation."
     },
     // ...
   ];
   ```

4. **Créer les liens** vers ce nouveau quiz :
   - Dans `doo/index.html` : ajouter une carte de quiz.
   - Dans la page principale `index.html` : ajouter une puce dans la liste des quiz de la carte DOO.

---

### 2. Ajouter un nouveau cours (ex: `algo/`)

1. **Créer le dossier** correspondant à la racine du projet :
   ```bash
   mkdir algo
   ```

2. **Créer une page d'accueil du module** `algo/index.html` (vous pouvez vous inspirer de `doo/index.html`).

3. **Ajouter la carte du cours sur la page principale** `index.html` :
   Insérer un bloc `<article class="course-card" ...>` dans la section `#courses-container` :
   ```html
   <article class="course-card" data-tags="all iai1 algo">
     <div class="course-header">
       <div class="course-meta">
         <span class="course-badge">IAI 1</span>
         <span class="status-badge active">
           <span class="status-indicator"></span> Actif
         </span>
       </div>
       <h3 class="course-title">Algorithmique & Structures de Données</h3>
       <span class="course-code">Module : /algo/</span>
     </div>
     <div class="course-body">
       <p class="course-desc">Complexité algorithmique, piles, files, arbres et graphes.</p>
       <!-- Liens vers les ressources ou quiz -->
     </div>
     <div class="course-footer">
       <a href="algo/index.html" class="btn btn-outline">Accéder au module →</a>
     </div>
   </article>
   ```

---

## 💻 Test en Local

Pour prévisualiser le site sur votre machine avant de pousser sur GitHub :

```bash
# Lancer un serveur HTTP simple avec Python 3
python3 -m http.server 8000
```

Ouvrez ensuite votre navigateur sur [http://localhost:8000](http://localhost:8000).

---

## 🚀 Déploiement sur GitHub Pages

Le déploiement est automatique à chaque `git push` sur la branche `main` :

1. Enregistrez et validez vos modifications :
   ```bash
   git add .
   git commit -m "Ajout de nouveaux quiz et mise à jour du portail"
   git push origin main
   ```
2. La mise à jour est en ligne en quelques secondes sur [https://cours-dg.github.io/](https://cours-dg.github.io/).

---

## 🎨 Charte Graphique & Typographies

- **Typographies :**
  - Titres et corps de texte : [*Outfit*](https://fonts.google.com/specimen/Outfit) (Google Fonts).
  - Code et étiquettes techniques : [*JetBrains Mono*](https://fonts.google.com/specimen/JetBrains+Mono).
- **Palette de couleurs principale :**
  - `--primary` : `#003366` (Bleu institutionnel)
  - `--secondary` : `#0077b6` (Bleu cyan)
  - `--accent` : `#e65100` (Orange dynamique pour les actions clés)
  - `--light-bg` : `#f8fafc` / fond dégradé doux `#f1f5f9` vers `#e2eafc`