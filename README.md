# 📊 Online Store — Analyse des Performances Commerciales (2023-2025)

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Power Query](https://img.shields.io/badge/Power%20Query-2C7CD6?style=for-the-badge&logo=microsoft&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)

---

## 📌 Contexte

Ce projet analyse les performances commerciales d'un Online Store sur la période **2023-2025**.  
Il part d'un fichier Excel brut de **1 200 commandes** et aboutit à un dashboard Power BI interactif.

---

## 🎯 Objectifs

- Évaluer les performances commerciales réelles de la boutique en ligne
- Analyser le comportement des commandes par statut (livré, annulé, retourné...)
- Identifier les produits et périodes les plus performants
- Calculer les KPIs clés pour une prise de décision éclairée

---

## 🗂️ Source de données

| Fichier | Description |
|---|---|
| `Online-Store-Orders.xlsx` | Dataset brut — 1 200 lignes, 14 colonnes |

**Colonnes principales :** `OrderID`, `Date`, `CustomerID`, `Product`, `Quantity`, `UnitPrice`, `PaymentMethod`, `OrderStatus`, `ItemsInCart`, `TotalPrice`

---

## 🛠️ Stack utilisé

| Outil | Usage |
|---|---|
| **Excel** | Source de données brute |
| **Power Query** | Nettoyage et transformation des données |
| **Power BI** | Modélisation, DAX et visualisation |

---

## 🔄 Méthodologie

### 1. Nettoyage des données (Power Query)
- Suppression des colonnes inutiles (`TrackingNumber`, `ShippingAddress`, `CouponCode`, `ReferralSource`)
- Correction des types de données
- Suppression des doublons sur `OrderID`
- Tri chronologique de la table `dim_Date`

### 2. Modélisation — Schéma en étoile

```
dim_Client       (CustomerID)
dim_Produit      (Product, UnitPrice)
dim_Date         (Date, Année, Mois_Num, Nom_Mois, Trimestre, Jour, Jour_Semaine)
dim_Paiement     (PaymentMethod)
dim_Statut       (OrderStatus)
        ↘       ↓       ↙
            fact_Orders
    (OrderID, Quantity, ItemsInCart, TotalPrice)
```

### 3. Mesures DAX créées

| Mesure | Description |
|---|---|
| `CA_Brut` | Somme totale de TotalPrice |
| `CA_Réel` | CA uniquement sur commandes livrées |
| `CA_Potentiel` | CA sur commandes livrées + expédiées |
| `Nbr_Transaction` | Nombre total de commandes |
| `Panier_Moyen` | CA Brut / Nbr_Transaction |
| `Taux_Annulation` | Nbr annulées / Nbr total |
| `Taux_Retour` | Nbr retournées / Nbr total |
| `Taux_Livraison` | Nbr livrées / Nbr total |
| `Taux_Expedition` | Nbr expédiées / Nbr total |

---

## 📊 KPIs clés

| Indicateur | Valeur |
|---|---|
| **CA Brut** | 1 264 761,96 |
| **CA Potentiel** | 488 760 |
| **CA Réel** | 242 600 |
| **Nombre de transactions** | 1 000 |
| **Panier Moyen** | 1 050 |
| **Taux d'annulation** | 20,83% |
| **Taux de retour** | 20,58% |
| **Taux de livraison** | 19,25% |

---

## 💡 Insights clés

- Moins de **20% du CA Brut** est réellement encaissé
- Le taux d'annulation + retour dépasse **41%** — signal d'alerte pour le business
- La **Chair** est le produit le plus vendu en CA Brut
- Le **pic d'activité** se situe en mai avec une chute notable en août
- Les 5 modes de paiement sont répartis de façon relativement équilibrée

---

## 📁 Structure du repository

```
online-store-powerbi/
│
├── Online-Store-Orders.xlsx     # Dataset source
├── projet3.pbix                 # Fichier Power BI
└── README.md                    # Documentation
```

---

## 👤 Auteur

**TANOE Mathieu Koffi**  
Data Analyst — Abidjan, Côte d'Ivoire  
🔗 [GitHub](https://github.com/tanoemathieu-dev)  
🔗 [LinkedIn](https://www.linkedin.com/in/tanoe-mathieu-koffi)

---

*Projet réalisé dans le cadre du développement de compétences en Data Analytics (Power BI, DAX, Power Query)*
