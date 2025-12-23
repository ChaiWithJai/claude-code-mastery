# Mortgage Calculator Service

A REST API for calculating mortgage payments, amortization schedules, and loan-to-value ratios.

## Architecture

```
mortgage-calc/
├── src/
│   ├── calculations/     # Pure functions for financial math
│   │   ├── payment.py    # Monthly payment calculations
│   │   ├── amortization.py
│   │   └── ratios.py     # LTV, DTI calculations
│   ├── validators/       # Input validation
│   │   └── loan_validator.py
│   ├── api/              # FastAPI routes
│   │   ├── routes.py
│   │   └── models.py     # Pydantic schemas
│   └── config.py         # Environment config
├── tests/
│   ├── test_calculations.py
│   └── test_api.py
└── scripts/
    └── deploy.sh
```

## Key Patterns

- **Pure calculations**: All financial math in `calculations/` is pure functions—no side effects, no I/O. This makes testing trivial and ensures correctness.

- **Decimal precision**: Financial amounts MUST use `Decimal` type, never floats. Floating point errors in money = angry customers.

- **Validation at boundary**: All input validation happens in `validators/` before data reaches calculations. Internal code assumes valid inputs.

## Development Workflow

1. Run tests: `pytest tests/ -v`
2. Start dev server: `uvicorn src.api.routes:app --reload`
3. Deploy: `./scripts/deploy.sh staging` (requires VPN)

## What NOT to Do

- **Never use floats for money**: Use `Decimal` from the decimal module. `0.1 + 0.2 != 0.3` in floats.

- **Never skip validation**: Even internal callers must go through validators. No "I know my input is good" shortcuts.

- **Never commit .env**: Contains database credentials. Use `.env.example` as template.
