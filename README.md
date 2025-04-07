<h1 align="center">Hi, I'm Carlos Cabrera Castrejón AKA:(Charly) <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="35"></h1>
<p align="center">
  <a href="https://readme-typing-svg.herokuapp.com">
    <img src="https://readme-typing-svg.herokuapp.com?font=Time+New+Roman&color=%23C8BE25&size=25&center=true&vCenter=true&width=600&height=100&lines=Data+Science+Coordinator+@Nestl%C3%A9;OOP+Teacher+@Universidad+Panamericana;Digital+Transformation+Leader;Agile+Scrum+Practitioner;Software+Engineer+%26+Data+Scientist" />
  </a>
</p>

<br>

<p align="center"> 
	<img src="https://komarev.com/ghpvc/?username=Carloscast09&label=Profile%20views&color=0047AB&style=plastic" alt="Carloscast09" height="25" width="160"/> 
</p>

<h2 align="center">About me</h2> 
<img alt="dsmark" align="right" height="50%" width="30%" src="https://c.tenor.com/NzrqQHFBVz8AAAAj/kitty-transparent.gif">


```sql
-- Creando la base de datos para mi perfil
CREATE DATABASE IF NOT EXISTS CharlyProfile;
USE CharlyProfile;

-- Tabla con información personal
CREATE TABLE PersonalInfo (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    alias VARCHAR(50),
    quick_bio TEXT,
    email VARCHAR(100),
    linkedin VARCHAR(255),
    github VARCHAR(255)
);

-- Tabla de roles profesionales
CREATE TABLE Roles (
    id INT PRIMARY KEY,
    person_id INT,
    title VARCHAR(100),
    company VARCHAR(100),
    is_primary BOOLEAN,
    FOREIGN KEY (person_id) REFERENCES PersonalInfo(id)
);

-- Tabla de habilidades técnicas
CREATE TABLE Skills (
    id INT PRIMARY KEY,
    person_id INT,
    skill_name VARCHAR(100),
    category VARCHAR(50),
    proficiency INT CHECK (proficiency BETWEEN 1 AND 10),
    FOREIGN KEY (person_id) REFERENCES PersonalInfo(id)
);

-- Tabla de proyectos actuales
CREATE TABLE Projects (
    id INT PRIMARY KEY,
    person_id INT,
    project_name VARCHAR(100),
    description TEXT,
    FOREIGN KEY (person_id) REFERENCES PersonalInfo(id)
);

-- Tabla de intereses de aprendizaje
CREATE TABLE LearningInterests (
    id INT PRIMARY KEY,
    person_id INT,
    interest VARCHAR(255),
    FOREIGN KEY (person_id) REFERENCES PersonalInfo(id)
);

-- Insertando mis datos personales
INSERT INTO PersonalInfo VALUES (
    1, 
    'Carlos Cabrera Castrejón', 
    'Charly',
    'Data Science Coordinator, OOP Teacher & Tech Enthusiast; apasionado por Agile, Python y la Transformación Digital.',
    'ccabreracastrejon@gmail.com',
    'https://www.linkedin.com/in/carlos-cabrera-cast/',
    'https://github.com/Carloscast09'
);

-- Insertando mis roles
INSERT INTO Roles VALUES 
(1, 1, 'Data Science Coordinator', 'Nestlé', TRUE),
(2, 1, 'OOP Teacher', 'Universidad Panamericana', FALSE);

-- Insertando mis habilidades
INSERT INTO Skills VALUES 
(1, 1, 'Python', 'Programming Language', 9),
(2, 1, 'SQL', 'Database', 9),
(3, 1, 'Power BI', 'Business Intelligence', 8),
(4, 1, 'Tableau', 'Data Visualization', 8),
(5, 1, 'Agile Scrum', 'Methodology', 9),
(6, 1, 'Digital Transformation', 'Strategy', 8);

-- Insertando mis proyectos actuales
INSERT INTO Projects VALUES 
(1, 1, 'Alice Talk', 'Desarrollo de LLM con RAG para consultas de negocio'),
(2, 1, 'Alice Tetris', 'Optimización de carga de camiones bajo Agile Scrum'),
(3, 1, 'Alice 360', 'Transformación digital para Purina');

-- Insertando mis intereses de aprendizaje
INSERT INTO LearningInterests VALUES 
(1, 1, 'Técnicas avanzadas de Data Science'),
(2, 1, 'Cloud Computing'),
(3, 1, 'Nuevas tecnologías emergentes');

-- Consulta para mostrar mi perfil completo
SELECT 
    p.name AS Nombre,
    p.alias AS Alias,
    p.quick_bio AS Bio,
    r.title AS Rol,
    r.company AS Empresa,
    GROUP_CONCAT(DISTINCT s.skill_name) AS Habilidades,
    GROUP_CONCAT(DISTINCT pr.project_name) AS Proyectos,
    GROUP_CONCAT(DISTINCT l.interest) AS 'Aprendiendo'
FROM 
    PersonalInfo p
    JOIN Roles r ON p.id = r.person_id
    JOIN Skills s ON p.id = s.person_id
    JOIN Projects pr ON p.id = pr.person_id
    JOIN LearningInterests l ON p.id = l.person_id
WHERE 
    r.is_primary = TRUE
GROUP BY 
    p.id, r.id;
```

## Mi Experiencia Profesional



- :office: **Data Science Coordinator @ Nestlé**  
  Lidero proyectos innovadores que integran inteligencia artificial y metodologías data-driven para optimizar la cadena de suministro. Destaco en proyectos como **Alice Talk** (desarrollo de LLM con RAG), **Alice Tetris** (optimización de carga de camiones bajo Agile Scrum) y **Alice 360** (transformación digital para Purina).

- :teacher: **OOP Teacher @ Universidad Panamericana**  
  Imparto clases de Programación Orientada a Objetos con Python, integrando metodologías ágiles para preparar a los estudiantes a desafíos reales.

- :computer: Apasionado por el **desarrollo de software**, la **ciencia de datos** y la **transformación digital**.

- :rocket: Siempre en la búsqueda de aprender nuevas tecnologías y perfeccionar metodologías de trabajo.

<br>

## <picture> <img src="https://github.com/7oSkaaa/7oSkaaa/blob/main/Images/Connect-with-me.gif?raw=true" width="100px"> </picture> ¡Conéctate conmigo!

<p align="center">
	<a href="mailto:ccabreracastrejon@gmail.com">
    <img src="https://img.shields.io/badge/gmail-%23EA4335.svg?style=plastic&logo=gmail&logoColor=white" alt="Gmail"/>
  </a>
	<a href="https://github.com/Carloscast09">
    <img src="https://img.shields.io/badge/github-%23181717.svg?style=plastic&logo=github&logoColor=white" alt="GitHub"/>
  </a>
	<a href="https://www.linkedin.com/in/carlos-cabrera-cast/">
    <img src="https://img.shields.io/badge/linkedin-%230A66C2.svg?style=plastic&logo=linkedin&logoColor=white" alt="LinkedIn"/>
  </a>
</p>

## 🛠️ Mis Habilidades Técnicas

### <picture> <img src="https://github.com/7oSkaaa/7oSkaaa/blob/main/Images/Programming_Languages.gif?raw=true" width="50px"> </picture> Lenguajes de Programación
<p align="center"> 
  &emsp; 
  <a href="https://www.python.org" target="_blank"> 
    <img alt="Python" src="https://img.shields.io/badge/Python-3776AB?style=plastic&logo=python&logoColor=white">
  </a> 
  &emsp;
  <a href="#">
    <img alt="SQL" src="https://img.shields.io/badge/SQL-4479A1?style=plastic&logo=postgresql&logoColor=white">
  </a> 
  &emsp;
  <a href="#">
    <img alt="PHP" src="https://img.shields.io/badge/PHP-777BB4?style=plastic&logo=php&logoColor=white">
  </a> 
  &emsp;
  <a href="#">
    <img alt="JavaScript" src="https://img.shields.io/badge/JavaScript-F7DF1E?style=plastic&logo=javascript&logoColor=black">
  </a> 
  &emsp;
  <a href="#">
    <img alt="C#" src="https://img.shields.io/badge/C%23-239120?style=plastic&logo=csharp&logoColor=white">
  </a>
  &emsp;
  <a href="#">
    <img alt="Java" src="https://img.shields.io/badge/Java-007396?style=plastic&logo=java&logoColor=white">
  </a>
</p>

### <picture> <img src="https://github.com/7oSkaaa/7oSkaaa/blob/main/Images/Software_Tools.gif?raw=true" width="50px"> </picture> Herramientas & Plataformas
<p align="center">
  &emsp;
    <a href="#">
      <img alt="Tableau" src="https://img.shields.io/badge/Tableau-E97627?style=plastic&logo=tableau&logoColor=white">
    </a>
  &emsp;
    <a href="#">
      <img alt="Power BI" src="https://img.shields.io/badge/Power%20BI-F2C811?style=plastic&logo=powerbi&logoColor=black">
    </a>
  &emsp;
    <a href="#">
      <img alt="SSRS" src="https://img.shields.io/badge/SSRS-4479A1?style=plastic">
    </a>
  &emsp;
    <a href="#">
      <img alt="SSIS" src="https://img.shields.io/badge/SSIS-4479A1?style=plastic">
    </a>
  &emsp;
    <a href="#">
      <img alt="Git" src="https://img.shields.io/badge/Git-F05032?style=plastic&logo=git&logoColor=white">
    </a>
</p>

### <picture> <img src="https://github.com/7oSkaaa/7oSkaaa/blob/main/Images/IDEs.gif?raw=true" width="50px"> </picture> Entornos de Desarrollo
<p align="center">
  &emsp;
    <a href="#">
      <img alt="Visual Studio Code" src="https://img.shields.io/badge/VS%20Code-0078D7?style=plastic&logo=visual-studio-code&logoColor=white">
    </a>
  &emsp;
    <a href="#">
      <img alt="JetBrains" src="https://img.shields.io/badge/JetBrains-000000?style=plastic&logo=jetbrains&logoColor=white">
    </a>
</p>

<br>

---

<details><summary><h3>🔥 Mis Rachas en GitHub</h3></summary>
<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Carloscast09&theme=tokyonight_duo" alt="Carloscast09" />
</p>
</details>

<details open>
<summary>
  <img src="https://media.giphy.com/media/cj87CxfRtrUifF3Ryk/giphy.gif" width="25">
  <b>Mis Rachas en GitHub</b>
</summary>

<br>

<h2 align="center">Carlos Cabrera Castrejón's GitHub Stats</h2>

<p align="center">
  <table>
    <tr>
      <td>
        <img width="400px" align="center" src="https://github-readme-stats.vercel.app/api?username=Carloscast09&show_icons=true&count_private=true&theme=tokyonight&hide_border=true" />
      </td>
      <td>
        <img width="400px" align="center" src="https://github-readme-streak-stats.herokuapp.com/?user=Carloscast09&theme=tokyonight&hide_border=true" />
      </td>
    </tr>
  </table>
</p>

<h2 align="center">Most Used Languages</h2>

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Carloscast09&langs_count=8&layout=compact&theme=tokyonight&hide_border=true" />
</p>

</details>

<details>
<summary>
  <img src="https://media.giphy.com/media/iY8CRBdQXODJSCERIr/giphy.gif" width="25">
  <b>GitHub Activity Graph</b>
</summary>
<br/>

<p align="center">
  <a href="https://github.com/Carloscast09">
    <img src="https://github-readme-activity-graph.vercel.app/graph?username=Carloscast09&theme=react-dark&hide_border=true&area=true" alt="Carloscast09's Activity Graph" width="100%">
  </a>
</p>

</details>

<details>
<summary>
  <img src="https://media.giphy.com/media/j2pOGeGYKe2xCCKwfi/giphy.gif" width="25">
  <b>3D Contribution Graph</b>
</summary>
<br/>

<p align="center">
  <img src="https://raw.githubusercontent.com/Carloscast09/Carloscast09/master/profile-3d-contrib/profile-night-rainbow.svg" alt="Carloscast09's 3D Contrib Chart" />
</p>

</details>

<details><summary><h3>⚡ Mi Actividad Reciente</h3></summary>
<p align="center">
  <img src="https://github-readme-activity-graph.cyclic.app/graph?username=Carloscast09&theme=github" alt="Carloscast09's activity graph"/>
</p>
</details>

<details><summary><h3>:trophy: Mis Trofeos en GitHub</h3></summary>
<p align="center">
  <a href="https://github.com/ryo-ma/github-profile-trophy">
    <img src="https://github-profile-trophy.vercel.app/?username=Carloscast09&layout=compact&theme=tokyonight&column=4&margin-w=15&margin-h=15" alt="Carloscast09" />
  </a>
</p>
</details>

<details><summary><h3>:open_file_folder: Mis Repositorios Destacados</h3></summary>
<div align="center">
  <p>
    <a href="https://github.com/Carloscast09/your-repo-1">
      <img src="https://github-readme-stats.vercel.app/api/pin/?username=Carloscast09&repo=your-repo-1&theme=tokyonight" alt="Repo 1" />
    </a>
    <a href="https://github.com/Carloscast09/your-repo-2">
      <img src="https://github-readme-stats.vercel.app/api/pin/?username=Carloscast09&repo=your-repo-2&theme=tokyonight" alt="Repo 2" />
    </a>
    <!-- Agrega más repositorios destacados según prefieras -->
  </p>
</div>
</details>

<br><br>

## 🐍 La Serpiente Devoradora de mis Contribuciones
	
<p align="center">
	<img src="https://github.com/7oSkaaa/7oSkaaa/blob/output/github-contribution-grid-snake.svg?" alt="Snake Game"/>
</p>