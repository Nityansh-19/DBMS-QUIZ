<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Database & ER Model Tough MCQ Quiz — Made by Nityansh</title>
  <style>
    :root{
      --bg:#0f1724;
      --card:#0b1220;
      --muted:#94a3b8;
      --accent:#06b6d4;
      --correct:#16a34a;
      --wrong:#dc2626;
      --glass: rgba(255,255,255,0.03);
    }
    *{box-sizing:border-box;font-family:Inter,ui-sans-serif,system-ui,-apple-system,'Segoe UI',Roboto,"Helvetica Neue",Arial;}
    body{
      margin:0;
      background: linear-gradient(180deg,#021226 0%, #081827 60%);
      color:#e6eef6;
      min-height:100vh;
      padding:24px;
      display:flex;
      align-items:flex-start;
      justify-content:center;
    }
    .container{
      width:100%;
      max-width:1000px;
    }
    header{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:16px;
      margin-bottom:18px;
    }
    .brand{
      background:var(--glass);
      padding:14px 16px;
      border-radius:12px;
      box-shadow:0 6px 18px rgba(2,6,23,0.6), inset 0 1px 0 rgba(255,255,255,0.02);
    }
    h1{margin:0;font-size:18px;letter-spacing:0.2px}
    .sub{
      font-size:13px;color:var(--muted);margin-top:6px;
    }
    .scorebox{
      background:linear-gradient(180deg, rgba(6,182,212,0.06), rgba(6,182,212,0.03));
      padding:12px 14px;border-radius:10px;text-align:right;min-width:220px;
    }
    .score{
      font-weight:700;font-size:18px;
    }
    .hint{font-size:12px;color:var(--muted);margin-top:6px}
    .quiz{
      margin-top:12px;
      display:grid;
      grid-template-columns:1fr 300px;
      gap:16px;
    }
    .questions{
      background:var(--card);
      padding:18px;border-radius:12px;box-shadow:0 10px 30px rgba(2,6,23,0.5);
      max-height:75vh; overflow:auto;
    }
    .panel{
      background:rgba(255,255,255,0.02);
      margin-bottom:12px;padding:12px;border-radius:10px;
    }
    .qnum{
      display:flex;justify-content:space-between;align-items:center;
      margin-bottom:8px;
    }
    .qtext{font-weight:600}
    .opts{display:grid;gap:8px;margin-top:8px}
    .opt{
      background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.007));
      padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.03);
      cursor:pointer;user-select:none;
      transition:all .15s;
    }
    .opt:hover{transform:translateY(-2px)}
    .opt.disabled{opacity:0.7;cursor:default;transform:none}
    .opt.correct{background:linear-gradient(90deg, rgba(16,185,129,0.14), rgba(16,185,129,0.06));border-color:rgba(16,185,129,0.4);box-shadow:0 6px 18px rgba(16,185,129,0.06)}
    .opt.wrong{background:linear-gradient(90deg, rgba(239,68,68,0.08), rgba(239,68,68,0.02));border-color:rgba(239,68,68,0.3);box-shadow:0 6px 18px rgba(239,68,68,0.03)}
    aside{
      position:sticky; top:18px;
      height:max-content;
    }
    .sidecard{
      background:var(--card);padding:16px;border-radius:12px;
      box-shadow:0 6px 18px rgba(2,6,23,0.45);
    }
    .final{
      margin-top:12px;padding:12px;border-radius:10px;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    }
    button{
      background:transparent;border:1px solid rgba(255,255,255,0.06);color:inherit;padding:10px 12px;border-radius:8px;cursor:pointer;
    }
    .footer{
      margin-top:14px;color:var(--muted);font-size:13px;text-align:center;
    }
    @media (max-width:880px){
      .quiz{grid-template-columns:1fr; }
      aside{position:relative}
    }
    /* small score badge */
    .badge{display:inline-block;padding:6px 8px;border-radius:999px;background:rgba(255,255,255,0.03);font-weight:600}
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="brand">
        <h1>Made by Nityansh</h1>
        <div class="sub">to pass score 40 or above</div>
      </div>

      <div class="scorebox">
        <div>Live Score</div>
        <div class="score" id="liveScore">0 / 50</div>
        <div class="hint">Answered: <span id="answered">0</span> &nbsp;|&nbsp; Remaining: <span id="remaining">50</span></div>
      </div>
    </header>

    <div class="quiz">
      <div class="questions" id="questions"></div>

      <aside>
        <div class="sidecard">
          <h3 style="margin:0 0 8px 0">Quiz Controls</h3>
          <div style="font-size:14px;color:var(--muted);margin-bottom:10px">Click an option to answer. Correct turns green; wrong turns red and reveals the correct option.</div>
          <div style="display:flex;gap:8px;margin-bottom:12px">
            <button id="showScoreBtn">Show Final Score</button>
            <button id="resetBtn">Reset Quiz</button>
          </div>
          <div class="final" id="finalBox">
            <div style="font-weight:700">Final Score</div>
            <div style="font-size:28px;margin-top:6px" id="finalScore">0 / 50</div>
            <div style="margin-top:8px;color:var(--muted)">Status: <span id="status">Not completed</span></div>
          </div>
        </div>
        <div style="height:12px"></div>
        <div class="sidecard" style="margin-top:12px">
          <div style="font-weight:700;margin-bottom:8px">Topics covered</div>
          <ul style="margin:0;padding-left:18px;color:var(--muted);font-size:14px;line-height:1.5">
            <li>DBMS vs File System, Advantages</li>
            <li>Data Models, Schemas, Instances</li>
            <li>Three-schema architecture & Data Independence</li>
            <li>DB Languages & Interfaces</li>
            <li>Classification of DBMS</li>
            <li>ER Model: Entities, Relationships, Keys, Constraints</li>
            <li>Weak Entities, Roles, Structural Constraints</li>
            <li>Extended ER features & Mapping to tables</li>
          </ul>
        </div>
      </aside>
    </div>

    <div class="footer">Good luck — answer carefully. (This quiz expects strong theoretical knowledge.)</div>
  </div>

<script>
/*
  50 tough MCQs covering:
  - Introduction to Databases (DBMS basics, architecture, schemas, data independence, DB languages, classification)
  - Entity-Relationship Model (keys, constraints, ER diagrams, weak entities, roles, mapping to relations)
*/
const questions = [
  {
    q: "Which of the following most accurately distinguishes a Database Management System (DBMS) from a simple file-based system?",
    opts: [
      "DBMS stores more data than files and runs faster.",
      "DBMS enforces data independence and supports complex queries via a high-level language, whereas file systems require application-level logic for data management.",
      "DBMS always uses SQL while file systems cannot store structured data.",
      "DBMS eliminates the need for backup and recovery unlike file systems."
    ],
    a: 1
  },
  {
    q: "Which statement best describes logical data independence?",
    opts: [
      "Ability to change the physical storage without changing the conceptual schema.",
      "Ability to change the conceptual schema without affecting external schemas or application programs.",
      "Ability to change user views without changing the conceptual schema.",
      "Ability to change external schemas without changing physical storage."
    ],
    a: 1
  },
  {
    q: "In the three-schema architecture, which layer defines the data structures used by the DBMS (tables, views) and the relationships among them?",
    opts: [
      "Internal schema",
      "External schema",
      "Conceptual schema",
      "Physical schema"
    ],
    a: 2
  },
  {
    q: "Which of these is NOT a primary responsibility of a DBMS DBMS component?",
    opts: [
      "Query processing and optimization",
      "Transaction management and concurrency control",
      "Automatic creation of application-specific user interfaces",
      "Recovery from system crashes and media failures"
    ],
    a: 2
  },
  {
    q: "Which data model is best described as using tuples, attributes, and relations as its core concepts?",
    opts: [
      "Hierarchical model",
      "Network model",
      "Relational model",
      "Object-oriented model"
    ],
    a: 2
  },
  {
    q: "Which of these is a correct distinction between schema and instance?",
    opts: [
      "Schema is the actual content at a moment; instance is the blueprint of database structure.",
      "Schema is static definition of structure; instance is the data stored at a particular time.",
      "Both are synonyms and mean the same.",
      "Instance changes rarely while schema changes frequently."
    ],
    a: 1
  },
  {
    q: "Which of the following is the strongest property of a superkey?",
    opts: [
      "It uniquely identifies tuples and is minimal.",
      "It uniquely identifies tuples but may not be minimal.",
      "It may not uniquely identify tuples but is minimal.",
      "It is solely used for foreign key references."
    ],
    a: 1
  },
  {
    q: "A candidate key differs from a primary key in that:",
    opts: [
      "Candidate key is chosen by the DBMS, primary key by the user.",
      "A candidate key is any minimal superkey; a primary key is one chosen candidate key to identify tuples uniquely.",
      "A candidate key cannot be composite whereas a primary key can be composite.",
      "There is no difference; they are identical terms."
    ],
    a: 1
  },
  {
    q: "Which constraint enforces that each value in a column is atomic (i.e., not a set or a record)?",
    opts: [
      "Referential integrity",
      "Entity integrity",
      "Domain constraint (atomicity within domain)",
      "Key constraint"
    ],
    a: 2
  },
  {
    q: "Which of the following best describes a weak entity set?",
    opts: [
      "An entity set with no attributes",
      "An entity set that cannot be uniquely identified by its own attributes alone and requires a supporting identifying relationship with an owner entity set.",
      "An entity set represented only in the internal schema",
      "An entity set that has more attributes than its owner"
    ],
    a: 1
  },
  {
    q: "In ER modelling, a relationship with degree > 2 is called:",
    opts: [
      "Unary relationship",
      "Binary relationship",
      "Ternary or n-ary relationship",
      "Composite relationship"
    ],
    a: 2
  },
  {
    q: "Which of the following is TRUE about referential integrity?",
    opts: [
      "A foreign key value must exist as a primary key value in the referenced relation, or be NULL if permitted.",
      "Primary keys can reference foreign keys in other tables.",
      "Referential integrity applies only to candidate keys, not primary keys.",
      "It only applies at the physical storage level."
    ],
    a: 0
  },
  {
    q: "Which is the best description of a view in the context of DBMS?",
    opts: [
      "A materialized copy of a table stored separately on disk.",
      "A virtual relation derived from base relations that can restrict and present data to users, possibly hiding base table complexities.",
      "An index on a particular attribute to speed up queries.",
      "A backup snapshot taken periodically."
    ],
    a: 1
  },
  {
    q: "Which language type is primarily responsible for database definition and schema creation?",
    opts: [
      "DML (Data Manipulation Language)",
      "DDL (Data Definition Language)",
      "DCL (Data Control Language)",
      "Query Language only"
    ],
    a: 1
  },
  {
    q: "Which of the following choices classifies DBMS by the number of users and machines (i.e., single user, multiuser, centralized, distributed)?",
    opts: [
      "Data model classification",
      "Architecture/classification based on deployment and users",
      "Transaction isolation classification",
      "Query language classification"
    ],
    a: 1
  },
  {
    q: "When converting ER diagram to relational schema, how is a many-to-many relationship typically represented?",
    opts: [
      "As a foreign key in one of the participating entity relations",
      "As a separate relation (junction table) containing foreign keys referencing the primary keys of participating entities",
      "It cannot be mapped to relations",
      "By duplicating attributes in both entity relations"
    ],
    a: 1
  },
  {
    q: "Which of these best describes the role of 'roles' in a relationship in ER modelling?",
    opts: [
      "Roles denote the attribute types used in a relationship.",
      "Roles identify how each participating entity participates in the relationship (its semantic part), especially when an entity set participates more than once.",
      "Roles are only used for weak entities.",
      "Roles specify the database user privileges."
    ],
    a: 1
  },
  {
    q: "Which of the following is a structural constraint often specified on relationships?",
    opts: [
      "Atomicity constraint",
      "Integrity constraint",
      "Cardinality constraint (e.g., one-to-many, many-to-many)",
      "Functional dependency"
    ],
    a: 2
  },
  {
    q: "Which of the following is an example of an extended ER feature?",
    opts: [
      "Normalization",
      "Generalization and specialization",
      "Normalization anomalies",
      "Query optimization hints"
    ],
    a: 1
  },
  {
    q: "Which of the following is TRUE about a composite attribute in ER model?",
    opts: [
      "It cannot be mapped to relational schema.",
      "It is an attribute that can be subdivided into meaningful subparts and is usually mapped to multiple columns in a relation.",
      "It is the same as a multivalued attribute.",
      "It must always be declared as primary key."
    ],
    a: 1
  },
  {
    q: "Which one describes a multivalued attribute and how to map it to relations?",
    opts: [
      "Single-valued attribute stored in same table as scalar",
      "Multivalued attributes require creating a separate relation with foreign key to owner entity and attribute values as rows",
      "They are stored as comma-separated values in one column",
      "They must be ignored during mapping"
    ],
    a: 1
  },
  {
    q: "Which isolation level ensures that transactions never see intermediate states of other transactions (i.e., prevents dirty reads)?",
    opts: [
      "Read Uncommitted",
      "Read Committed",
      "Repeatable Read",
      "None of the above"
    ],
    a: 1
  },
  {
    q: "Which of the following best captures the essence of 'data independence'?",
    opts: [
      "Users don't need to know database internals to write application code because DBMS provides an abstracted view of data.",
      "Data can be accessed only by a single user at a time.",
      "Physical data layout never changes.",
      "Applications must be rewritten whenever physical schema changes."
    ],
    a: 0
  },
  {
    q: "A relation schema R(A,B,C) has a functional dependency A → B and B → C. Which of the following is logically implied?",
    opts: [
      "A → C (transitive dependency)",
      "C → A",
      "B → A",
      "No dependency can be derived"
    ],
    a: 0
  },
  {
    q: "Which of the following statements about primary keys is correct?",
    opts: [
      "A primary key may contain NULL values.",
      "A primary key uniquely identifies rows and cannot contain NULL.",
      "A primary key must be numeric.",
      "A table can have multiple primary keys."
    ],
    a: 1
  },
  {
    q: "Which DBMS classification term describes a DBMS that stores parts of the database on multiple physical machines cooperating to present a single logical database?",
    opts: [
      "Centralized DBMS",
      "Distributed DBMS",
      "Hierarchical DBMS",
      "In-memory DBMS"
    ],
    a: 1
  },
  {
    q: "If an entity set 'Employee' has attributes {EmpID, Name, DeptID} and Dept is another entity, the attribute DeptID in Employee is best modeled as:",
    opts: [
      "Derived attribute",
      "Primary key",
      "Foreign key referencing Dept's key",
      "Multivalued attribute"
    ],
    a: 2
  },
  {
    q: "Which of the following most correctly describes the difference between conceptual schema and external schema?",
    opts: [
      "Conceptual schema describes user's view; external schema is DB-wide.",
      "External schema is DB-wide; conceptual schema is physical storage.",
      "Conceptual schema is the global logical structure; external schema defines specific user views.",
      "They are synonymous."
    ],
    a: 2
  },
  {
    q: "What is the outcome when you enforce entity integrity on a relation?",
    opts: [
      "All foreign keys must be unique.",
      "Primary key columns cannot be NULL, ensuring each tuple is uniquely identifiable.",
      "No two rows can have the same non-key values.",
      "All columns must have a domain constraint."
    ],
    a: 1
  },
  {
    q: "Which of the following choices is a reason to use normalization?",
    opts: [
      "To increase data redundancy to improve performance",
      "To remove insertion, deletion and update anomalies by organizing attributes into relations based on functional dependencies",
      "To obfuscate the schema",
      "To convert conceptual schema to external schema"
    ],
    a: 1
  },
  {
    q: "Which of these best explains 'design issues' in ER modelling?",
    opts: [
      "Technical storage layout decisions",
      "How to model relationships, keys, weak entities, aggregation, and mapping choices that capture real-world constraints",
      "Only the naming conventions of attributes",
      "Only the choice of primary key"
    ],
    a: 1
  },
  {
    q: "Which of the following mapping rules is correct for a 1:1 relationship between two strong entity sets?",
    opts: [
      "Create a new relation for relationship with both primary keys as composite primary key only",
      "Add foreign key of one entity into the other (optionally as primary key) or create separate relation; choice depends on participation and totality constraints",
      "1:1 relationships cannot be represented in relational model",
      "Both entities must be merged into one relation always"
    ],
    a: 1
  },
  {
    q: "Which of the following is an example of a semantic constraint that might be captured in ER model but not enforced by DBMS without extra logic?",
    opts: [
      "Primary key constraint",
      "Check constraint on an attribute range",
      "Business rule like 'an employee cannot supervise more than 10 direct reports' requiring triggers or application logic",
      "Foreign key constraint"
    ],
    a: 2
  },
  {
    q: "Which of these DB languages is typically used by applications to request authorization to perform actions (like GRANT/REVOKE)?",
    opts: [
      "DML",
      "DDL",
      "DCL",
      "TCL"
    ],
    a: 2
  },
  {
    q: "While mapping weak entities to relations, which of these is true?",
    opts: [
      "Weak entity becomes independent relation without referencing owner.",
      "Weak entity relation includes foreign key to owner entity and may include owner key as part of its primary key.",
      "Weak entity's attributes are always embedded in owner's relation.",
      "Weak entities are ignored in mapping."
    ],
    a: 1
  },
  {
    q: "Which of the following statements about ER diagrams is false?",
    opts: [
      "ER diagrams can represent subclass/superclass relationships (specialization).",
      "ER diagrams can express participation constraints (total/partial).",
      "ER diagrams always specify exact storage mechanisms and indexes.",
      "ER diagrams can include attributes, composite and multivalued."
    ],
    a: 2
  },
  {
    q: "Which normalization form requires that there is no transitive dependency for non-prime attributes?",
    opts: [
      "1NF",
      "2NF",
      "3NF",
      "BCNF"
    ],
    a: 2
  },
  {
    q: "Which of these would you choose to store a derived attribute in a database?",
    opts: [
      "Never store derived attribute; always compute on demand, unless performance needs justify materialization.",
      "Always store derived attributes redundantly.",
      "Derived attributes must be primary keys.",
      "Derived attributes are stored in the internal schema only and not accessible."
    ],
    a: 0
  },
  {
    q: "What is the main purpose of transaction management subsystem in DBMS?",
    opts: [
      "To schedule backups",
      "To ensure ACID properties, manage concurrency, and provide recovery support",
      "To design ER diagrams",
      "To convert schema to physical file formats only"
    ],
    a: 1
  },
  {
    q: "If a relation R has candidate keys K1 and K2, a valid primary key selection rule is:",
    opts: [
      "Select any candidate key as primary key; remaining candidate keys are alternate keys.",
      "You must combine K1 and K2 to make a composite primary key.",
      "Primary key must be numeric so choose K1 only if numeric.",
      "Both candidate keys must be set as primary keys simultaneously."
    ],
    a: 0
  },
  {
    q: "Which of the following is a drawback of mapping every ER relationship as a separate relation?",
    opts: [
      "It may create many relations causing join-heavy queries and performance overhead.",
      "It always violates normalization rules.",
      "It is not allowed by relational model.",
      "It prevents use of foreign keys."
    ],
    a: 0
  },
  {
    q: "In an ER diagram, aggregation is used when:",
    opts: [
      "We want to group attributes into a composite attribute only.",
      "We want to treat a relationship set as an entity set to relate it to other entities (higher-level abstraction).",
      "We want to enforce referential integrity.",
      "We want to create multivalued attributes."
    ],
    a: 1
  },
  {
    q: "Which of the following most correctly describes 'classification of DBMS' by data models?",
    opts: [
      "Classifying DBMS solely by hardware vendor",
      "Classifying DBMS into relational, hierarchical, network, object-oriented, document, key-value based on underlying data model",
      "Classifying DBMS by UI look-and-feel",
      "Classifying DBMS depending on license only (open/closed)"
    ],
    a: 1
  },
  {
    q: "When should you use a composite key in a relational schema generated from ER model?",
    opts: [
      "When the entity has a single attribute primary key only",
      "When uniqueness of tuples is determined by combination of multiple attributes or when mapping weak entities requiring owner keys inclusion",
      "Composite keys are never recommended",
      "Only when there are duplicate attribute names"
    ],
    a: 1
  },
  {
    q: "Which mapping approach is usually used for modelling an ISA (subclass) hierarchy in relational schema to avoid redundancy but keep type-specific columns?",
    opts: [
      "Single table with all attributes (single relation approach)",
      "One table per subclass plus one for superclass (class table inheritance), or store whole thing in superclass table depending on trade-offs",
      "Do not map subclasses",
      "Always use separate relation for each attribute"
    ],
    a: 1
  },
  {
    q: "Which of the following represent a typical advantage of DBMS classification as 'distributed DBMS' over 'centralized DBMS'?",
    opts: [
      "Easier to maintain only one backup",
      "Improved availability and local autonomy, potential performance improvements via local data access",
      "No need for concurrency control",
      "No requirement for schema definition"
    ],
    a: 1
  },
  {
    q: "Which is the correct way to handle multi-valued relationship attributes when mapping to relations?",
    opts: [
      "Store them in the same tuple separated by delimiters",
      "Create a separate relation to hold multiple values with a foreign key to the owner",
      "Ignore them",
      "Convert them to composite attributes"
    ],
    a: 1
  },
  {
    q: "Which of these is most likely to be a 'design issue' when modeling keys in ER design?",
    opts: [
      "Choice of key attributes that remain stable over time and are minimal, avoiding natural keys that may change",
      "Choosing attribute names only",
      "Deciding colors in ER diagram",
      "Choosing font size"
    ],
    a: 0
  },
  {
    q: "Which of the following statements about conceptual schema evolution is correct?",
    opts: [
      "Conceptual schema never changes once finalized.",
      "Changes to conceptual schema aim to minimize effect on external schemas and application programs (logical data independence), but sometimes adaptations are needed.",
      "Conceptual schema must be identical to external schema.",
      "Changes to conceptual schema always require rewriting all SQL queries."
    ],
    a: 1
  },
  {
    q: "Which constraint or design element would you use to enforce 'at most one manager per department' when mapping ER model to relational schema?",
    opts: [
      "A foreign key that allows duplicates",
      "A uniqueness constraint on the manager attribute in department relation, or set manager as a candidate key",
      "No constraint is possible",
      "Use multivalued attribute"
    ],
    a: 1
  },
  {
    q: "Which of these is typically NOT stored in the internal schema of a DBMS?",
    opts: [
      "Indexes and storage allocation",
      "File organization and access paths",
      "User-friendly views (external schemas)",
      "Low-level record placement strategies"
    ],
    a: 2
  }
];

// sanity: should be 50 questions
if(questions.length !== 50){
  console.warn("Question count is not 50. Current:", questions.length);
}

// state
let score = 0;
let answeredCount = 0;
const questionsEl = document.getElementById('questions');
const liveScoreEl = document.getElementById('liveScore');
const answeredEl = document.getElementById('answered');
const remainingEl = document.getElementById('remaining');
const finalScoreEl = document.getElementById('finalScore');
const statusEl = document.getElementById('status');

function renderQuestions(){
  questionsEl.innerHTML = '';
  questions.forEach((q, idx)=>{
    const panel = document.createElement('div');
    panel.className = 'panel';
    panel.dataset.index = idx;

    // header
    const qnum = document.createElement('div');
    qnum.className = 'qnum';
    qnum.innerHTML = `<div style="font-size:13px;color:var(--muted)">Q${idx+1}</div><div style="font-size:13px;color:var(--muted)">Topic: DB/ER</div>`;
    panel.appendChild(qnum);

    const qtext = document.createElement('div');
    qtext.className = 'qtext';
    qtext.textContent = q.q;
    panel.appendChild(qtext);

    const opts = document.createElement('div');
    opts.className = 'opts';

    q.opts.forEach((optText, optIdx)=>{
      const opt = document.createElement('div');
      opt.className = 'opt';
      opt.tabIndex = 0;
      opt.dataset.q = idx;
      opt.dataset.opt = optIdx;
      opt.textContent = String.fromCharCode(65 + optIdx) + ". " + optText;
      opt.addEventListener('click', onOptionClick);
      opt.addEventListener('keydown', (e)=>{
        if(e.key === 'Enter' || e.key === ' '){ e.preventDefault(); opt.click(); }
      });
      opts.appendChild(opt);
    });

    panel.appendChild(opts);
    questionsEl.appendChild(panel);
  });
}

function onOptionClick(e){
  const optEl = e.currentTarget;
  if(optEl.classList.contains('disabled')) return;
  const qIdx = Number(optEl.dataset.q);
  const chosen = Number(optEl.dataset.opt);
  const question = questions[qIdx];
  const correct = question.a;

  // disable all options for this question after click
  const panel = optEl.closest('.panel');
  const allOpts = panel.querySelectorAll('.opt');

  // if already answered prevent double counting (safety)
  if(panel.dataset.answered === 'true') return;

  panel.dataset.answered = 'true';
  answeredCount++;
  answeredEl.textContent = answeredCount;
  remainingEl.textContent = questions.length - answeredCount;

  // correct case
  if(chosen === correct){
    optEl.classList.add('correct');
    score++;
    liveScoreEl.textContent = `${score} / ${questions.length}`;
  } else {
    // mark chosen wrong and mark correct
    optEl.classList.add('wrong');
    // find correct option element
    allOpts.forEach(o=>{
      const idx = Number(o.dataset.opt);
      if(idx === correct){
        o.classList.add('correct');
      }
    });
    liveScoreEl.textContent = `${score} / ${questions.length}`;
  }

  // disable pointer and keyboard navigation on option set
  allOpts.forEach(o=>{
    o.classList.add('disabled');
    o.removeEventListener('click', onOptionClick);
  });

  // update final area if all answered
  if(answeredCount === questions.length){
    updateFinal();
  }
}

function updateFinal(){
  finalScoreEl.textContent = `${score} / ${questions.length}`;
  statusEl.textContent = (score === questions.length) ? "PASS (50/50) 🎉" : (score > 0 ? "Fail — try again" : "Fail");
  // scroll to final
  document.getElementById('finalBox').scrollIntoView({behavior:'smooth'});
}

document.getElementById('showScoreBtn').addEventListener('click', ()=>{
  // show current final summary
  updateFinal();
  alert(`Current score: ${score} / ${questions.length} \\nAnswered: ${answeredCount} / ${questions.length}`);
});

document.getElementById('resetBtn').addEventListener('click', ()=>{
  if(!confirm('Reset quiz? Your progress will be lost.')) return;
  // reset state
  score = 0;
  answeredCount = 0;
  liveScoreEl.textContent = `0 / ${questions.length}`;
  answeredEl.textContent = '0';
  remainingEl.textContent = questions.length.toString();
  finalScoreEl.textContent = `0 / ${questions.length}`;
  statusEl.textContent = 'Not completed';
  // re-render
  renderQuestions();
});

renderQuestions();
liveScoreEl.textContent = `0 / ${questions.length}`;
answeredEl.textContent = '0';
remainingEl.textContent = questions.length.toString();
finalScoreEl.textContent = `0 / ${questions.length}`;
statusEl.textContent = 'Not completed';
</script>
</body>
</html>
