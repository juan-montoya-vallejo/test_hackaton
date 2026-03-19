# Suggested Tree (Example)

```text
.
├─ src/
│  ├─ bronze/                 # Transformations and cleanup for Bronze
│  ├─ silver/                 # Normalization/validation for Silver
│  └─ gold/                   # Final entity ("Golden Record") for Gold
│
│  # If you choose Python, you can keep 1 or more modules per layer:
│  ├─ bronze/
│  │  ├─ transform.py
│  │  └─ *.py                 # 1 or more files based on complexity
│  ├─ silver/
│  │  ├─ normalize.py
│  │  └─ *.py                 # 1 or more files based on complexity
│  └─ gold/
│     ├─ build_golden.py
│     └─ *.py                 # 1 or more files based on complexity
│
├─ docs/
│  ├─ legacy-legend/         # RAG context / references for the app
│  └─ prompt-journal/        # Prompt log used (if it applies to your implementation)
│
├─ scripts/
│  ├─ run-migration.(js|py|ts|sh)   # Pipeline orchestration
│  └─ validate-fidelity.(js|py|ts|sh)
│
├─ tests/
│  └─ dq/
│     ├─ schema.test.(js|py|ts)
│     └─ fidelity.test.(js|py|ts)
│
├─ artifacts/
│  ├─ lineage/
│  └─ reports/
│
└─ .github/
   └─ ISSUE_TEMPLATE/        # (optional) repository templates/guides
```

## Recommended Practices (Python)

- Prioritize **TDD**: write tests in `tests/` first, then implement in `src/`.
- Prioritize **OOP**: encapsulate layer rules in small classes with clear responsibilities.
- It is valid to start with 1 file per layer and expand to multiple modules if needed.

## Python Variant (1 or More Files)

```text
.
├─ src/
│  ├─ pipeline.py                    # Minimal option: one Python file
│  ├─ bronze.py                      # Modular option: 1..n Python files
│  ├─ silver.py
│  ├─ gold.py
│  └─ services/
│     ├─ llm_client.py               # Classes/services (OOP)
│     └─ validators.py
│
├─ tests/
│  ├─ test_pipeline.py               # TDD: write tests before implementation
│  ├─ test_bronze.py
│  ├─ test_silver.py
│  └─ test_gold.py
│
└─ docs/
   └─ prompt-journal/
```

## Recommendations

- **TDD first:** define expected tests before writing production code.
- **Use OOP when it adds clarity:** encapsulate business rules in small cohesive classes.
- **Scale gradually:** start with one Python file and split into modules as the project grows.

