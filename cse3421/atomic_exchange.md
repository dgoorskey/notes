# CSE3421: Meeting 2023-09-07

## Calling conventions
1. caller puts parameters in expected places (e.g. `$a0` - `$a3` registers)
2. caller transfers control to callee after saving return address (e.g. in `$ra` register)
3. callee acquires storage resources needed
4. callee performs task
5. callee puts result values in expected places (e.g. `$v0` - `$v1` registers)
6. callee returns control to callercaller

### Spilling registers
- what if callee needs to use more registers than just the argument and return values?
- callee uses a stack
- stack grows downward
- `$sp` register tracks the stack

### Heap allocation
- static data segment for constants and other static variables
- **heap:** tree-based structure (e.g. b-tree)
    - stack pointer is `$gp`
- **memory heap**: dynamic data segment for structures that grow and shrink

## Atomic exchange support
- **data race:** multiple threads access the same memory at the same time, and at least one of them is writing to it
- **atomic exchange (atomic swap):** atomically swap a value in register for a value in memory
    - implementation needs both a memory read and memory write in a single, uninterruptible instruction
    - alternative: a pair of specially configured instructions (e.g. `sc` and `ll` in MIPS)
        - `ll`: load memory into register
        - `sc`: try to store register to memory, if memory value was changed since the `ll` instruction, fail and return `0` in `$t0` instead

## MIPS instruction class distribution

| instruction class | integer frequency | float frequency |
|---|---|---|
| arithmetic | 16% | 48% |
| data transfer | 35% | 36% |
| logical | 12% | 4% |
| conditional branch | 34% | 8% |
| jump | %2 | ?% |

## Instruction cycle
1. fetch instruction
2. decode instruction
3. execute instruction
4. get memory
5. write to register

## Chipset comparison between Kirin 9000 and Kirin 9000s
- Kirin 9000s made by SMIC (China) in 7nm
    - 2.62 GHz Arm Cortex-A710, 140 mm^2
    - 25% more power
    - needs big cooling plate
- Kirin 9000 made by TSMC (Taiwan) in 5nm, 3 years ago
    - 3.13 GHz Arm Cortex-A710, 106 mm^2
