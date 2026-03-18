<!-- # 🧠 The Index -->

<!-- # <img src="./img/Index-logo.png" width="100" /> The index -->

# <p align="center" style="display: flex; align-items: center; justify-content: center; gap: 12px;">

  <img src="./img/Index-logo.png" width="60" />
  <span style="font-size: 28px; font-weight: 700;">The Index</span>
</p>

**The Index** is a creator-first registry platform designed to structure artist identity, artworks, and collections into a cohesive, system-driven interface with optional blockchain integration.

It shifts focus away from collections alone and toward the artist as the primary entity.

---

## ⚙️ Core Stack

- **Frontend:** Next.js
- **Backend:** Express.js
- **Database:** MongoDB
- **Storage:** Cloudinary (or S3-compatible)
- **Authentication:** JWT (HTTP-only cookies)
- **Blockchain:** Modular, chain-agnostic service layer

---

## 🏗️ Architecture Overview

```txt
the-index/
│
├── client/ # Next.js frontend
│ ├── app/
│ │ ├── page.js # Landing page
│ │ ├── artists/
│ │ │ ├── page.js
│ │ │ └── [slug]/page.js
│ │ ├── works/
│ │ │ └── [id]/page.js
│ │ ├── collections/
│ │ │ └── [slug]/page.js
│ │ ├── dashboard/
│ │ └── api-proxy/
│ │
│ ├── components/
│ ├── lib/
│ └── public/
│
├── server/ # Express backend
│ ├── src/
│ │ ├── config/
│ │ ├── models/
│ │ ├── routes/
│ │ ├── controllers/
│ │ ├── services/
│ │ ├── middleware/
│ │ └── app.js
│ │
│ └── server.js
│
└── README.md
```

## Technology Stack

- **Next.js** handles UI, routing, and public pages
- **Express** handles business logic and APIs
- **MongoDB** stores structured data
- **Storage** manages media assets
- **Blockchain layer** handles optional minting

---

## 📁 Project Structure

```txt
the-index/
│
├── client/ # Next.js frontend
│ ├── app/
│ │ ├── page.js
│ │ ├── artists/
│ │ │ ├── page.js
│ │ │ └── [slug]/page.js
│ │ ├── works/
│ │ │ └── [id]/page.js
│ │ ├── collections/
│ │ │ └── [slug]/page.js
│ │ ├── dashboard/
│ │ └── api-proxy/
│ │
│ ├── components/
│ ├── lib/
│ └── public/
│
├── server/ # Express backend
│ ├── src/
│ │ ├── config/
│ │ ├── models/
│ │ ├── routes/
│ │ ├── controllers/
│ │ ├── services/
│ │ ├── middleware/
│ │ └── app.js
│ │
│ └── server.js
│
└── README.md
```

---

## 🧩 Core Data Models

### ArtistProfile

```js
{
  (userId,
    displayName,
    slug,
    bio,
    avatarUrl,
    bannerUrl,
    links,
    blockchainPreferences,
    verified,
    createdAt,
    updatedAt);
}
```

---

### Artwork

```js
{
  (artistId,
    title,
    slug,
    description,
    imageUrl,
    medium,
    year,
    tags,
    collectionId,
    status, // draft | published | minted
    blockchainRecordId,
    metadata,
    createdAt,
    updatedAt);
}
```

---

### Collection

```js
{
  (artistId,
    title,
    slug,
    description,
    coverImageUrl,
    artworkIds,
    createdAt,
    updatedAt);
}
```

---

### Blockchain Record

```js
{
  (artworkId,
    chain,
    contractAddress,
    tokenId,
    transactionHash,
    metadataUri,
    mintedAt,
    status);
}
```

---

### 🔌 API Design

**_Auth_**

POST /api/auth/register
POST /api/auth/login
GET /api/auth/me

---

**_Artist_**

GET /api/artists
GET /api/artists/:slug
POST /api/artists
PATCH /api/artists/:id

---

**_Artworks_**

GET /api/artworks
GET /api/artworks/:id
POST /api/artworks
PATCH /api/artworks/:id
DELETE /api/artworks/:id

---

**_Collections_**

GET /api/collections
GET /api/collections/:slug
POST /api/collections
PATCH /api/collections/:id

---

**_Uploads_**

POST /api/uploads/image

---

**_Blockchain_**

POST /api/blockchain/mint
GET /api/blockchain/record/:artworkId

---

### 🧠 Design Philosophy

Artist-first, not collection-first

Structured identity over anonymous minting

Separation of display and system logic

Chain-agnostic architecture

Extensible for future creative tooling

The platform treats artists as indexed entities, not just wallets.

---

### 🚀 Development Phases

Phase 1 — Core Registry

Artist profiles

Artwork uploads

Collections

Public pages

Phase 2 — Creator Dashboard

Profile editing

Artwork management

Draft/publish workflow

Phase 3 — Blockchain Integration

Minting pipeline

Metadata handling

Provenance display

Phase 4 — Discovery Layer

Search & filtering

Tags & categories

Featured artists

Verification system

---

### 🧭 Future Expansion

Multi-chain support

Collector profiles

Licensing systems

Public API access

Integration with Origin OS

---

### 🧩 Summary

The Index is not just a gallery.

It is a structured registry of creators, their works, and their digital provenance.

A system where:

identity is preserved

context is visible

creation is traceable
