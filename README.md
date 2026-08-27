<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:07152E,45:0D47A1,100:00B8D4&height=220&section=header&text=Charly%20Cabrera&fontSize=46&fontColor=FFFFFF&animation=fadeIn&fontAlignY=36&desc=Data%20Engineer%20%E2%80%A2%20Data%20Warehouse%20%E2%80%A2%20Azure%20Databricks&descAlignY=58&descSize=17" width="100%" alt="Charly Cabrera — Data Engineer" />
</p>

<p align="center">
  <a href="https://readme-typing-svg.herokuapp.com">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=500&size=22&duration=3200&pause=900&color=38BDF8&center=true&vCenter=true&width=760&lines=Turning+business+rules+into+data+products;Building+governed+Data+Warehouse+solutions;Designing+DataOps+workflows+for+Databricks;Connecting+business%2C+engineering+and+architecture" alt="Typing introduction" />
  </a>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/carlos-cabrera-cast/">
    <img src="https://img.shields.io/badge/LinkedIn-Let's_connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  <a href="mailto:ccabreracastrejon@gmail.com">
    <img src="https://img.shields.io/badge/Email-Say_hello-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
  </a>
  <img src="https://komarev.com/ghpvc/?username=Carloscast09&label=PROFILE+VIEWS&color=0D47A1&style=for-the-badge" alt="Profile views" />
</p>

<img align="right" width="245" alt="Animated coding cat" src="https://c.tenor.com/NzrqQHFBVz8AAAAj/kitty-transparent.gif" />

👋 About me

I'm Carlos Cabrera Castrejón, but everyone calls me Charly.

I'm a Data Warehouse Specialist at Profuturo, where I work across data modeling, engineering, automation, and platform architecture on Azure Databricks.

I enjoy the point where a messy business problem becomes a clear technical design: defining the grain, modeling facts and dimensions, building reliable transformations, adding quality controls, and making the result understandable and useful.

I have delivered data initiatives across financial services, supply chain, pharmaceuticals, and consulting. I also teach university-level data and programming courses—because understanding something deeply and explaining it clearly are two sides of the same skill.

<br clear="right" />

🗄️ charly_profile database

<p align="center">
  <img src="https://img.shields.io/badge/MODEL-STAR_SCHEMA-38BDF8?style=for-the-badge&logo=databricks&logoColor=white" alt="Star schema" />
  <img src="https://img.shields.io/badge/GRAIN-ONE_ENGINEER-0D47A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="One engineer grain" />
  <img src="https://img.shields.io/badge/STATUS-ALWAYS_LEARNING-00B8D4?style=for-the-badge&logo=googlegemini&logoColor=white" alt="Always learning" />
</p>

<details open>
<summary><b>▶ Run profile_model.sql</b></summary>

<br />

-- ============================================================================
-- CHARLY_PROFILE
-- A tiny dimensional model of my professional journey
-- Grain: one row per role, capability, or measurable impact
-- Platform: Databricks SQL
-- ============================================================================

CREATE SCHEMA IF NOT EXISTS charly_profile;
USE SCHEMA charly_profile;

-- ---------------------------------------------------------------------------
-- DIMENSION: Who is the engineer behind the data?
-- ---------------------------------------------------------------------------
CREATE OR REPLACE TEMP VIEW dim_engineer AS
SELECT * FROM VALUES
    (
        1,
        'Carlos Cabrera Castrejón',
        'Charly',
        'Data Warehouse Specialist',
        'Profuturo',
        'Business problems → reliable, governed data products',
        TRUE
    )
AS engineer (
    engineer_sk,
    full_name,
    alias,
    current_role,
    current_company,
    professional_mission,
    always_learning
);

-- ---------------------------------------------------------------------------
-- DIMENSION: The roles that shaped the journey
-- ---------------------------------------------------------------------------
CREATE OR REPLACE TEMP VIEW dim_role AS
SELECT * FROM VALUES
    (1, 1, 'Data Warehouse Specialist',  'Profuturo',                'Financial Services', TRUE),
    (2, 1, 'University Professor',        'Universidad Panamericana','Education',          TRUE),
    (3, 1, 'Data Science Coordinator',    'Nestlé',                   'Supply Chain',       FALSE),
    (4, 1, 'Data Visualization Lead',     'NYX',                      'Consulting',         FALSE),
    (5, 1, 'Business Systems Analyst',    'IQVIA',                    'Pharmaceuticals',    FALSE)
AS role (
    role_sk,
    engineer_sk,
    role_name,
    organization,
    business_domain,
    is_current
);

-- ---------------------------------------------------------------------------
-- DIMENSION: Capabilities—not arbitrary proficiency percentages
-- ---------------------------------------------------------------------------
CREATE OR REPLACE TEMP VIEW dim_capability AS
SELECT * FROM VALUES
    (1,  'Language',      'Python'),
    (2,  'Language',      'SQL'),
    (3,  'Processing',    'PySpark'),
    (4,  'Platform',      'Azure Databricks'),
    (5,  'Architecture',  'Data Warehousing'),
    (6,  'Architecture',  'Dimensional Modeling'),
    (7,  'Engineering',   'ETL / ELT'),
    (8,  'Engineering',   'Data Quality'),
    (9,  'DataOps',       'CI/CD'),
    (10, 'DataOps',       'Databricks Asset Bundles'),
    (11, 'Integration',   'REST APIs & OAuth M2M'),
    (12, 'Leadership',    'Business ↔ Technology Translation')
AS capability (
    capability_sk,
    capability_group,
    capability_name
);

CREATE OR REPLACE TEMP VIEW bridge_engineer_capability AS
SELECT
    1 AS engineer_sk,
    capability_sk
FROM dim_capability;

-- ---------------------------------------------------------------------------
-- FACT: A few measurable outcomes from the journey
-- ---------------------------------------------------------------------------
CREATE OR REPLACE TEMP VIEW fct_career_impact AS
SELECT * FROM VALUES
    (1, 3, 'Dashboard migration',                  15D, 'dashboards',        'Preserved KPIs and business continuity'),
    (2, 3, 'Processing and delivery improvement', 50D, 'percent reduction', 'Automated Supply Chain data workflows'),
    (3, 4, 'AWS data pipeline delivery',           10D, 'pipelines',         'Built with AWS Glue and Amazon S3'),
    (4, 4, 'ETL processing improvement',           40D, 'percent reduction', 'Accelerated analytical data delivery'),
    (5, 5, 'SQL Server data scale',                78D, 'million records',   'Supported pharmaceutical market products'),
    (6, 5, 'Monitor production improvement',       33D, 'percent reduction', 'Automated ETL validation and auditing')
AS impact (
    impact_sk,
    role_sk,
    impact_name,
    metric_value,
    metric_unit,
    business_context
);

-- ---------------------------------------------------------------------------
-- PROFILE QUERY: The current version of Charly
-- ---------------------------------------------------------------------------
SELECT
    e.alias,
    e.current_role,
    e.current_company,
    CONCAT_WS(' · ', SORT_ARRAY(COLLECT_SET(c.capability_name))) AS capabilities,
    e.professional_mission,
    e.always_learning
FROM dim_engineer e
JOIN bridge_engineer_capability b
    ON e.engineer_sk = b.engineer_sk
JOIN dim_capability c
    ON b.capability_sk = c.capability_sk
GROUP BY ALL;

</details>

🚀 What I'm working on

<table>
  <tr>
    <td width="50%" valign="top">
      <h3>🏗️ Data Warehouse & Lakehouse</h3>
      <p>Dimensional modeling, business grain, Silver-to-Gold transformations, historical data, lineage, and governed publication layers.</p>
    </td>
    <td width="50%" valign="top">
      <h3>⚙️ Production Data Engineering</h3>
      <p>PySpark and SQL pipelines, idempotent reprocessing, validation, observability, data quality, and maintainable engineering patterns.</p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3>🔄 DataOps for Databricks</h3>
      <p>GitHub workflows, CI/CD, Databricks Asset Bundles, environment promotion, traceability, validation, and rollback strategies.</p>
    </td>
    <td width="50%" valign="top">
      <h3>🔐 Platform & Architecture</h3>
      <p>REST APIs, Databricks Apps, service principals, OAuth M2M, Unity Catalog, and secure Azure connectivity patterns.</p>
    </td>
  </tr>
</table>

🧭 My journey in a nutshell

🏦 Profuturo — Data Warehouse, Azure Databricks, DataOps, integrations, platform troubleshooting, and architecture.

🍫 Nestlé — Data and analytics for Supply Chain, Databricks, Machine Learning enablement, Power BI, and functional coordination of a four-person team.

☁️ NYX — AWS data pipelines, solution POCs, QuickSight, and direct people management.

💊 IQVIA — Pharmaceutical market data, ETL automation, data quality, governance, SQL Server, SSIS, Python, and C#.

🎓 Universidad Panamericana — Teaching, mentoring, and turning complex technical topics into practical learning experiences.

🛠️ Tech constellation

<h3 align="center">Languages & processing</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/SQL-336791?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL" />
  <img src="https://img.shields.io/badge/PySpark-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white" alt="PySpark" />
  <img src="https://img.shields.io/badge/Apache_Spark-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white" alt="Apache Spark" />
  <img src="https://img.shields.io/badge/C%23-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" alt="C#" />
</p>

<h3 align="center">Data platforms & cloud</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Azure_Databricks-FF3621?style=for-the-badge&logo=databricks&logoColor=white" alt="Azure Databricks" />
  <img src="https://img.shields.io/badge/Delta_Lake-00ADD8?style=for-the-badge&logo=databricks&logoColor=white" alt="Delta Lake" />
  <img src="https://img.shields.io/badge/Unity_Catalog-1B63A9?style=for-the-badge&logo=databricks&logoColor=white" alt="Unity Catalog" />
  <img src="https://img.shields.io/badge/Microsoft_Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Microsoft Azure" />
  <img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white" alt="AWS" />
</p>

<h3 align="center">Engineering, delivery & analytics</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git" />
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" alt="GitHub Actions" />
  <img src="https://img.shields.io/badge/CI%2FCD-0B1026?style=for-the-badge&logo=githubactions&logoColor=white" alt="CI/CD" />
  <img src="https://img.shields.io/badge/REST_APIs-005571?style=for-the-badge&logo=fastapi&logoColor=white" alt="REST APIs" />
  <img src="https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" alt="Power BI" />
</p>

🌱 Currently leveling up

01. Production-grade PySpark and Apache Spark internals
02. Reusable DataOps patterns for Azure Databricks
03. Secure data-platform integrations and cloud networking
04. Causal inference and applied machine learning

[!NOTE]
Most of my recent work lives in enterprise environments and cannot be published directly. The examples I share use synthetic data and sanitized architectures to preserve confidentiality while keeping the engineering decisions real.

📊 GitHub pulse

<details open>
  <summary><b>Stats, languages and activity</b></summary>
  <br />
  <p align="center">
    <img height="170" src="https://github-readme-stats.vercel.app/api?username=Carloscast09&show_icons=true&theme=tokyonight&hide_border=true&rank_icon=github" alt="Charly's GitHub stats" />
    <img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Carloscast09&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" alt="Most used languages" />
  </p>
  <p align="center">
    <img src="https://github-readme-activity-graph.vercel.app/graph?username=Carloscast09&theme=tokyo-night&hide_border=true&area=true" width="100%" alt="Charly's contribution graph" />
  </p>
</details>

<details>
  <summary><b>🌌 3D contribution universe</b></summary>
  <br />
  <p align="center">
    <img src="https://raw.githubusercontent.com/Carloscast09/Carloscast09/master/profile-3d-contrib/profile-night-rainbow.svg" width="100%" alt="Charly's 3D contribution chart" />
  </p>
</details>

☕ Let's build something useful

<p align="center">
  I enjoy conversations about <b>Data Engineering</b>, <b>Data Warehousing</b>, <b>Databricks</b>, <b>DataOps</b>, and <b>cloud architecture</b>.
</p>

<p align="center">
  <a href="mailto:ccabreracastrejon@gmail.com">
    <img src="https://img.shields.io/badge/Write_to_me-ccabreracastrejon%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email Charly" />
  </a>
  <a href="https://www.linkedin.com/in/carlos-cabrera-cast/">
    <img src="https://img.shields.io/badge/Find_me_on-LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="Connect on LinkedIn" />
  </a>
</p>

<p align="center">
  <i>Curious by default. Structured by design. Always learning.</i>
</p>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:07152E,45:0D47A1,100:00B8D4&height=120&section=footer" width="100%" alt="Footer" />
