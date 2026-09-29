# Lab 2 — Bonus: Authentication Flow Risk Analysis

## Severity table

The authentication-focused model produced **22 risks** in total.

| Severity | Count |
|---|---:|
| High | 1 |
| Elevated | 5 |
| Medium | 12 |
| Low | 4 |
| **Total** | **22** |

---

## Risks surfaced by the feature-level authentication model

The following risks appeared in the authentication-focused model but did not appear in the baseline architecture model.

| Rule ID | Severity | STRIDE | Mitigation |
|---|---:|---|---|
| `sql-nosql-injection` | **High** | **T — Tampering** | Use parameterized queries / prepared statements and never construct database queries directly from user-controlled input. |
| `unguarded-access-from-internet` | **Elevated** | **E — Elevation of Privilege** | Protect Internet-facing authentication components with an appropriate gateway/proxy layer, access controls, request validation and rate limiting. |
| `unguarded-direct-datastore-access` | **Elevated** | **E — Elevation of Privilege** | Restrict datastore access to a dedicated least-privileged identity and expose only the operations required by the authentication flow. |

### `sql-nosql-injection`

Observed risk:

```text
RULE: sql-nosql-injection
SEVERITY: high
TITLE: SQL/NoSQL-Injection risk at Login Endpoint against database Credential Store via Validate Credentials
ASSET: login-endpoint
```

The feature-level model explicitly represents the flow:

```text
Login Endpoint
      |
      | Validate Credentials
      v
Credential Store
```

This makes the database interaction visible to the threat model, allowing the SQL/NoSQL injection risk to be identified.

---

### `unguarded-access-from-internet`

Observed risks:

```text
Unguarded Access from Internet of Login Endpoint by User Browser via Submit Login
```

and:

```text
Unguarded Access from Internet of Token Verification by User Browser via Present Token
```

These appear because the feature-level model explicitly exposes the authentication components that receive requests originating from the user-controlled browser.

---

### `unguarded-direct-datastore-access`

Observed risk:

```text
RULE: unguarded-direct-datastore-access
SEVERITY: elevated
TITLE: Unguarded Direct Datastore Access of Credential Store by Login Endpoint via Validate Credentials
ASSET: credential-store
```

The detailed model shows a direct relationship between the `Login Endpoint` and the `Credential Store`, which was hidden inside the broader `Juice Shop Application` asset in the architecture-level model.

---

## What the feature-level model revealed

The feature-level model exposes security-sensitive responsibilities that were hidden inside the single `Juice Shop Application` component in the architecture-level model, such as credential validation, token issuing, token verification and administrative authorization.

Because these responsibilities and their communication links are modeled separately, the threat model can identify authentication-specific risks such as SQL/NoSQL injection against the credential store and unguarded access paths that the higher-level architecture model could not represent explicitly.
