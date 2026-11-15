# Outline of the presentation

## Intro

## Motivation

## Problem

## Solution

We introduce a git-like versioning system for Rhino documents. 
The data storage layer is abstracted and replaceable. We implemented file system storage. 
Clients communicate with the server via a REST API. 

## How it works

- Every Rhino object, layer, material, block definition, … is an **entity** keyed by its Rhino GUID.
- Each entity version is an immutable **manifest** (named component blobs + references), addressed by its SHA-256 hash.
- A **commit** points to a Merkle tree (document → kind → 256 shards → entries), so commits and diffs cost time proportional to the change.
- The server validates every commit and merge (references, layer tree, unique names, settings) and moves branches only by compare-and-swap, so clients cannot create an invalid snapshot.


