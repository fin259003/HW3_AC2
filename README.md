-- Homomorphic Encryption Battleship--

A simple but concise privacy-preserving Battleship game implemented using Paillier Homomorphic Encryption.
Each player has their own hidden 10×10 board with ships, and all hit/miss checks are performed without revealing board contents.

Homework Overview

This homework implements a two-player Battleship game where:
- Each player has a 10×10 board
- Ships of sizes 5, 4, 3, 2, and 2 are automatically placed
- Players take turns firing shots
- The game continues until one player’s entire fleet is destroyed
- All hit/miss checks use homomorphic encryption
- The goal is to ensure that no player can see the opponent’s board, while still allowing the game to function normally.

This homework uses the Paillier cryptosystem, which supports operations on encrypted values.
This allows the game to verify HIT or MISS without decrypting the board cell.

Each board cell is either:

0 → water
1 → ship

When a player fires at a coordinate:

1. The cell value is encrypted
2. A random blinding multiplier k is applied (homomorphically)
3. The blinded value is decrypted

| Cell      | Encrypted Value | After * k | Decrypted Result |
| --------- | --------------- | --------- | ---------------- |
| 0 (water) | Enc(0)          | Enc(0)    | 0 → MISS         |
| 1 (ship)  | Enc(1)          | Enc(k)    | k (≠0) → HIT     |

The attacker never sees:
- The real board
- Any unblinded encrypted values
- Any structural information
- They only learn hit or miss.

Features
-Two players: Alice and Bob

-Independent 10×10 Battleship boards

-Ships: 5, 4, 3, 2, 2

-Automatic ship placement (no overlap)

-Turn-based gameplay with hit/miss feedback

-Game statistics after each turn

-Win detection when all ship cells are hit

-Secure hit/miss verification using Paillier Homomorphic Encryption



