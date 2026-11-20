# MaintiDoc – Livrable 1 : cadrage, corpus et architecture

Module IA générative multimodale · EMSI-2026

## Membres de l'équipe

- Issam BENLAAMA (travail individuel)

Nom d'équipe : **BENLAAMA**

## Objectif du projet

MaintiDoc est un assistant documentaire pour techniciens de maintenance. Il répond à des questions techniques (texte et photo) à partir de documents autorisés, **en citant la page et la figure d'origine**. Il peut consulter l'historique d'un équipement via un outil MCP et préparer un ticket, **créé uniquement après approbation humaine**. Il ne pilote aucun équipement et ne garantit aucun diagnostic.

Contexte choisi : une chaîne fictive de collecte de données de match dans un stade fictif (Atlas Arena). Les équipements documentés produisent les données ; le calcul de statistiques est hors périmètre.

Familles d'équipements :
1. `capteurs_suivi` : caméras TrackEye T4 (unités UT-T4), gilets PulseVest V2, dock PulseDock D1
2. `collecte_donnees` : consoles TagStation C3, serveur de fusion MergeServer M1

Tous les produits, utilisateurs, tickets et historiques sont **fictifs**. Le corpus est **100 % synthétique** (généré avec Claude, vérifié par contrôles automatiques ; relecture humaine à finaliser : colonne `verifie_par`).

## Contenu du ZIP

```
L1_MaintiDoc_BENLAAMA.zip
└── L1_MaintiDoc_BENLAAMA/
    ├── L1_MaintiDoc_BENLAAMA_Rapport.pdf      rapport complet (parties 2.1 à 2.6)
    ├── L1_MaintiDoc_BENLAAMA_LienGitHub.txt   URL du dépôt GitHub
    ├── README.md                            ce fichier
    └── L1_MaintiDoc_BENLAAMA_Corpus/
        ├── inventaire.csv                   40 lignes, 20 colonnes
        ├── prompts_corpus.md                prompts P01 à P17 et analyse critique
        ├── documents/famille_1/             17 PDF
        ├── documents/famille_2/             18 PDF
        └── images/                          5 images de panneaux
```

Les fichiers du corpus sont nommés `<document_id>.<extension>`, avec le même `document_id` que dans `inventaire.csv`.

## Structure du dépôt GitHub

```
maintidoc/
├── README.md
├── .gitignore
├── docs/
│   └── diagrammes/        sources Mermaid (.mmd) et images (.png)
└── corpus/
    ├── inventaire.csv
    ├── prompts_corpus.md
    ├── documents/famille_1/
    ├── documents/famille_2/
    └── images/
```

## Groupes d'accès fictifs

| Groupe | Voit |
|---|---|
| `techniciens_capteurs` | famille 1 et documents partagés |
| `techniciens_collecte` | famille 2 et documents partagés |
| `responsables` | tous les documents |

## Documents prévus pour les tests de la semaine 5

- Contradictoires : `proc_remplacement_camera_v1` / `v2`, `proc_redemarrage_service_fusion_v1` / `v2`
- Injection de prompt : `note_service_piegee`
- Ambigus : photos de voyants orange, SYNC ERROR (caméra et console), seuils de dérive 20 ms et 50 ms
