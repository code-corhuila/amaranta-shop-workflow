# amaranta-shop-workflow

> Business process orchestration (saga)

Part of the **Amaranta Shop** distributed system — team `amaranta-shop`, Grupo 2.
Governance and documentation live in [`amaranta-shop-docs`](https://github.com/code-corhuila/amaranta-shop-docs).

## Branching

Three permanent branches. **None of them accepts a direct commit** — you enter through a child
branch and leave through a Pull Request.

```
develop  <--PR--  feat/... fix/... chore/...
qa       <--PR--  qa/...
main     <--PR--  release/...  hotfix/...
```

Promotion happens **by re-application** (`git cherry-pick -x`), never by merging one permanent
branch into another: `merge develop -> qa` and `merge qa -> main` do not exist in this model.

`main` requires **1 approval from `ariel5253`**. On `develop` and `qa` the team sets its own review
rule.

Full policy: `00-governance/branching-policy.md` in `amaranta-shop-docs`.

## Role in the system

Orchestration of the processes that cross domains, and above all what is undone when a step fails: the checkout saga (reserve stock, create the order, compensate on failure).

## Depends on

`amaranta-shop-sales-api` and `amaranta-shop-catalog-api`; the public key and a service token from `amaranta-shop-security`.

## How to run

Nothing to run yet. Once the code lands: `mvn -B verify` to build and test, `mvn spring-boot:run` to start it with the variables of `.env.example`.

## Stack

Planned: Java 21, from the teacher's `workflow-java` template. The language of each transversal is confirmed in the ADR of the stack when it is built.

## Status

**Skeleton.** Only the base of a code repository is here (norm 5.1); nothing in it runs yet, and this README says so
on purpose. Next pull request: `feat/checkout-saga`: the checkout saga with its compensations, tests first.
