# Assembly Expressions
- individual terms:
    - constants
    - user-defined symbols
    - special terms (e.g. `*` for location counter)
- expressions are evaluated at assemble time
- **absolute expression:**
    - contains only absolute terms
    - contains relative terms that occur in pairs, have the opposite sign, and aren't used in multiplication or division (e.g. `Buff2 - Buff1` gives an absolute result)
- **relative expressions:**
    - all relative terms can be paired except one
    - the remaining unpaired term is positive
    - ???
