# AI Assistant Knowledge Base

**Last Updated**: 2025-11-12
**Project**: Lux TSS
**Organization**: Lux Industries

## Project Overview

Lux TSS is a production-ready implementation of multi-party threshold signature schemes (TSS) for ECDSA and EdDSA. This library enables secure distributed key management where multiple parties collaborate to generate signatures without any single party having access to the complete private key. Based on the Gennaro-Goldfeder 2018 research paper.

## Essential Commands

### Development
```bash
# Install dependencies
go mod download

# Run tests
make test

# Generate pre-parameters for testing
go run test/preParams_test.go

# Build documentation
cd docs && pnpm install && pnpm build

# Run benchmarks
go test -bench=. ./...
```

## Architecture

### Core Components
- **ECDSA**: Full implementation of threshold ECDSA (secp256k1)
- **EdDSA**: Full implementation of threshold EdDSA (Edwards25519)
- **Common**: Shared protocol infrastructure (parties, messages, rounds)
- **Crypto**: Cryptographic primitives (Paillier, VSS, ZKPs, MTA)

### Protocol Structure
- **Keygen**: Distributed key generation without trusted dealer
- **Signing**: Threshold signing using key shares
- **Resharing**: Dynamic group changes and share refresh

### Security Features
- Feldman VSS for verifiable secret sharing
- Multiple zero-knowledge proofs (Schnorr, DLN, Range)
- Paillier encryption for MTA protocol
- Commitment schemes to prevent equivocation

## Key Technologies

- **Language**: Go 1.19+
- **Curves**: secp256k1 (ECDSA), Edwards25519 (EdDSA)
- **Crypto**: math/big, crypto/elliptic, custom implementations
- **Protocols**: GG18 (Gennaro-Goldfeder 2018)
- **Documentation**: Fumadocs, Next.js 16, MDX

## Development Workflow

### Testing Approach
1. Unit tests for each cryptographic primitive
2. Integration tests for complete protocols
3. Concurrent party simulation tests
4. Property-based testing for invariants

### Code Organization
```
/ecdsa/         - ECDSA implementation
  /keygen/      - Key generation protocol
  /signing/     - Signing protocol
  /resharing/   - Resharing protocol
/eddsa/         - EdDSA implementation (parallel structure)
/crypto/        - Cryptographic primitives
/common/        - Shared utilities
/tss/           - Core TSS abstractions
/docs/          - Documentation site
```

## Documentation Updates (2025-11-12)

### Enhanced Documentation
- **index.mdx**: Comprehensive introduction with architecture diagrams, protocol flows, use cases
- **api.mdx**: Complete API reference with all core types, functions, and examples
- **security.mdx**: Detailed security guide covering threat model, best practices, vulnerabilities
- **getting-started.mdx**: Step-by-step tutorial with working code examples

### Documentation Build
- Successfully configured Fumadocs with Next.js 16
- Fixed frontmatter validation issues
- Build output: 7 static pages generated
- Location: `/docs/.next/` (production build ready)

## Context for All AI Assistants

This file (`LLM.md`) is symlinked as:
- `.AGENTS.md`
- `CLAUDE.md`
- `QWEN.md`
- `GEMINI.md`

All files reference the same knowledge base. Updates here propagate to all AI systems.

## Rules for AI Assistants

1. **ALWAYS** update LLM.md with significant discoveries
2. **NEVER** commit symlinked files (.AGENTS.md, CLAUDE.md, etc.) - they're in .gitignore
3. **NEVER** create random summary files - update THIS file

---

**Note**: This file serves as the single source of truth for all AI assistants working on this project.
