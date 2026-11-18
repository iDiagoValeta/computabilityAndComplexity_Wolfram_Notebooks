# computabilityAndComplexity_Wolfram_Notebooks

**Four Wolfram Mathematica lab assignments on formal languages, register machines, cellular automata and P systems, kept as PDF exports of the notebooks, plus the course handouts they answer.**

> **Context.** Built in May 2025 as coursework for Computability and Complexity (CMC) at UPV, when I was finishing my Computer Engineering degree (Computing specialization) and working as a guide and workshop instructor at the UPV Computer Museum. It is one of my first public repositories. It is kept as it was submitted; the code is not maintained.

## What it does

- Generates and checks context-free grammars: finds the nonterminals that directly produce a string of terminals, and those whose every production contains the nonterminal itself, and decides whether a string belongs to a grammar with the CYK algorithm.
- Implements the macros of a RAM (register) machine as Mathematica modules over an external memory list, and uses them to build small arithmetic programs.
- Simulates one-dimensional elementary cellular automata from a rule number, Conway's Game of Life with animated generations, and left-unidirectional cellular automata that accept or reject strings.
- Simulates two P systems (membrane computing): a probabilistic one run for a number of transitions, and one that tests divisibility of a number by k.
- Includes the original course handouts (in Spanish) that define each assignment.

## How it works

Each assignment is a Mathematica notebook that was exported to PDF with its code and printed outputs. The notebooks themselves (`.nb`) are not in the repository.

1. **Grammars** (`grammar_Generation_And_Verification.pdf`). A grammar is a list `{nonterminals, terminals, productions, start}`. `directamenteGenerativos` and `directamenteNoGenerativos` scan the productions; `formaNormalChomsky[gram, w]` fills the CYK table for a grammar in Chomsky normal form and checks that the start symbol is in the top cell.
2. **RAM macros** (`macros_RAM.pdf`). Instructions such as `suc`, `pre`, `cer`, `asi`, `cop`, `sum`, `mul`, `div`, `mei` and `ig` modify a global `memoria` list (addresses start at 1). Four exercise functions `f1` to `f4` and a helper `f5` (power) are composed from them: a power with a square-root exponent, a logarithm of an antilogarithm, a square root, and a power of one number by another.
3. **Cellular automata** (`cellular_Automata_Exploration.pdf`). `GenerarPatronBinario` expands a rule number (0 to 255) into its neighbourhood table, `EstadoSiguiente` applies it with wrap-around edges and `EjecutarAC` iterates it; history is drawn with `ArrayPlot` and `ListAnimate`. `ContarEntorno` and `EvolucionarVida` do the same for the Game of Life, tried on a glider, a glider gun, a still life and an oscillator. `AceptarPorIzquierda` runs a unidirectional automaton over an input string.
4. **P systems** (`p_Systems_Simulation.pdf`). `RunP1b[n]` applies a random rule up to n times and prints the contents of membrane 2. `RunDivisibilityP[n, k]` simulates the membrane rules for divisibility and returns the final multisets of regions 1 and 3.

## Results

Printed outputs taken from the notebook exports:

- Grammar examples: `directamenteGenerativos` returns `{B, S}`, `{A}`, `{A, B}` and `{A, B, S}` for the four example grammars; `directamenteNoGenerativos` returns `{A}`, `{B, C}`, `{}` and `{F}` (`grammar_Generation_And_Verification.pdf`).
- CYK: `formaNormalChomsky[Ejemplo3, {a, a, b, b}]` is `True` and `{a, a, a, b}` is `False`; for `Ejemplo4`, `{a, b, a, b, a}` and `{b, b, b, a, b, b, b}` are `True` and `{a, a, a, b}` is `False`.
- Left-unidirectional automata: `AceptarPorIzquierda` accepts `{a, b, b, b}` and rejects `{b, a, a, b}` for the first automaton (`cellular_Automata_Exploration.pdf`).
- P system divisibility: with k = 5, n = 20, 5, 500 end with `s` in region 3 and n = 17, 4, 16 end with `n` (`p_Systems_Simulation.pdf`).

## Run it

There is nothing to execute from this repository: only PDFs are included. To reproduce the work you would need Wolfram Mathematica (or the Wolfram Engine) and would have to retype the code from the PDFs, since the `.nb` files are not provided. I did not run any of it for this README.

Suggested reading order, which follows the course practices:

1. `bulletins/Gramaticas.pdf`, then `grammar_Generation_And_Verification.pdf`
2. `bulletins/Máquinas de registros.pdf`, then `macros_RAM.pdf`
3. `bulletins/Autómatas celulares.pdf`, then `cellular_Automata_Exploration.pdf`
4. `bulletins/SistemasP.pdf`, then `p_Systems_Simulation.pdf`

## Repository layout

```
grammar_Generation_And_Verification.pdf   Practice 1 notebook export: grammars and CYK
macros_RAM.pdf                            Practice 2 notebook export: RAM machine macros
cellular_Automata_Exploration.pdf         Practice 3 notebook export: cellular automata
p_Systems_Simulation.pdf                  Practice 4 notebook export: P systems
bulletins/                                Course handouts for practices 1 to 4 (Spanish)
```

The practice numbers come from the titles of the handouts in `bulletins/`.

## Stack

Wolfram Mathematica (Wolfram Language), exported to PDF.
