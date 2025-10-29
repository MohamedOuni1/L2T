# [Fonctionnalités détaillées de l’API HTTP SMS v0](https://app.algeriesms.com/login)

[![Logo SMS](https://i.ibb.co/Hfhr4gTz/LOGO-sms.png)](https://www.tunisiesms.tn/)

## 🌟 Présentation de l’API

L’API HTTP SMS d’AlgérieSMS v0 de [L2T](https://www.l2t.io/) permet d’automatiser l’envoi, le suivi et la gestion des messages SMS via une interface simple accessible par des requêtes HTTP.

---

## 1️⃣ Envoi de SMS en temps réel

### 🏷️ Description
Cette fonctionnalité permet d’envoyer des SMS instantanément à un ou plusieurs destinataires. L’envoi est immédiat dès la réception de la requête, et le serveur renvoie un code d’état confirmant la réussite ou l’échec de l’opération.

### ⚙️ Points clés
- Envoi instantané de messages vers un ou plusieurs numéros.  
- Prise en charge du format international des numéros (ex. 21612345678).  
- Possibilité de personnaliser le nom d’expéditeur (`sender`).  
- Gestion des caractères spéciaux (encodage UTF-8).  
- Réception d’un `message_id` unique pour chaque envoi (utile pour le suivi).

---

## 2️⃣ Envoi programmé (planification)

### 🏷️ Description
L’API offre la possibilité de programmer l’envoi de SMS à une date et une heure spécifique grâce aux paramètres date et heure.

### ⚙️ Points clés
- Planification d’envois à une date/heure future.  
- Idéal pour les campagnes marketing ou rappels automatisés.  
- Les paramètres date (format jj/mm/aaaa) et heure (format hh:mm) sont facultatifs.  
- Si non renseignés, l’envoi est immédiat.

---

## 3️⃣ Gestion des expéditeurs (sender ID)

### 🏷️ Description
Le `sender` correspond au nom qui s’affiche sur le téléphone du destinataire à la place du numéro. Seuls les expéditeurs déclarés et validés par [L2T](https://www.l2t.io/) peuvent être utilisés, afin d’éviter tout abus (spam, usurpation, etc.).

### ⚙️ Points clés
- Utilisation uniquement d’expéditeurs approuvés par [L2T](https://www.l2t.io/).  
- Peut être un nom d’entreprise, une abréviation, ou un numéro court.

---

## 4️⃣ Gestion du contenu du SMS

### 🏷️ Description
Le paramètre `sms` contient le texte du message. L’API gère les caractères standards GSM et peut envoyer des messages longs (multi-part) sur demande.

### ⚙️ Points clés
- Encodage UTF-8 pour tous les caractères.  
- Taille standard : 160 caractères par SMS.  
- Messages longs disponibles sur demande via [L2T](https://www.l2t.io/).  
- Support des caractères spéciaux : é, à, ç, etc.

---

## 5️⃣ Suivi et récupération des accusés de réception (DLR)

### 🏷️ Description
Chaque SMS envoyé génère un `message_id` unique pour permettre le suivi de la livraison via la fonctionnalité DLR (Delivery Receipt).

### ⚙️ Points clés
- Vérification du statut de livraison des messages.  
- Identification des messages non remis, expirés ou rejetés.  
- Réponse au format XML pour chaque `message_id`.  
- Possibilité de vérifier plusieurs `msg_id` dans une seule requête (séparés par `;`).

### 🧩 États possibles des messages SMS

| Statut       | Signification                                   |
|--------------|------------------------------------------------|
| DELIVERED    | Message livré avec succès                       |
| UNDELIVERED  | Message non remis                               |
| EXPIRED      | Message expiré avant livraison                 |
| REJECTED     | Message rejeté (blacklist, STOP SMS)          |
| UNKNOWN      | Livraison en attente de confirmation           |

---

## 6️⃣ Codes d’état (Status Codes)

### 🏷️ Description
Chaque requête retourne un code HTTP indiquant le résultat de l’opération. Ces codes permettent de gérer les erreurs dans vos applications.

### ⚙️ Points clés
- `2xx` → Succès  
- `4xx` → Erreurs liées à la requête (clé, format, contenu…)  
- `5xx` → Erreur serveur

---

## 7️⃣ Sécurité et authentification

### 🏷️ Description
L’accès à l’API est sécurisé par une clé unique attribuée à chaque compte client.

### ⚙️ Points clés
- La clé (`key=...`) est obligatoire dans chaque requête.  
- Requête sans clé valide → `401 - Non autorisée`.  
- La clé possède une date d’expiration.  
- Utiliser des variables d’environnement pour protéger la clé.

---

## 8️⃣ Gestion du quota et du solde

### 🏷️ Description
L’API contrôle le solde SMS et le quota journalier pour éviter les abus et assurer la disponibilité du service.

### ⚙️ Points clés
- `402` → Solde insuffisant  
- `420` → Quota journalier dépassé

---

## 9️⃣ Support et maintenance

Un support technique est disponible pour toute assistance (activation multi-SMS, ajout d’expéditeur, etc.) via [L2T](https://www.l2t.io/).

### 🧾 Coordonnées

|  Type       | Détails                          |
|---------------|------------------------------------|
| ✉️ Email      | [support@L-2T.com](mailto:support@L-2T.com) |
| 📞 Téléphone  | +216 31 17 19 17                   |
| 🏢 Commercial | +216 27 22 99 99                   |
| ⏰ Horaires   | Lundi – Vendredi : 9h00 → 15h00   |

---

## 📝 Licence

![Licence](https://img.shields.io/badge/Licence-Propri%C3%A9taire-blue)

© 2025 **[L2T](https://www.l2t.io/)**. Tous droits réservés.  
Ce document et son contenu sont la **propriété exclusive** de **[L2T](https://www.l2t.io/)**
Toute reproduction, distribution ou utilisation sans autorisation écrite est strictement interdite.

