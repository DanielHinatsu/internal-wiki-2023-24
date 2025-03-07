# Encoding and Decoding

[ADD CITATIONS]

## Encoding: 
- consists of segmenting information into blocks, generating primers, mapping primers back to address space and generating all the sequences to be encoded in wet lab.

### Algorithm design for primers:
1. Distance constraints
   - Run edit distance and Levenshtein distance constraints on all primers once in a while
2. Biological constraints
   - Length: 18 - 30 bases
    - 40 - 60% GC content
    - GC clamp at 3’ end of primer, stronger more specific binding
  - Annealing and melting temperature 
    - T_m - 5 = T_a
    - Forward and reverse should have same/similar temps
    - Calculate melting temperature: 4 for every G/C, 2 for every A/T
    - Secondary structures
    - Use established tools to avoid hairpins, self-dimers, cross-dimers
    - Avoid mispriming
    - Avoid repeats on the 3’ end

#### Encoding Formats
1. Naive encoding:
   - Encode to base 4
2. Ternary to bases (Aachen encoding):
   - encoding density is less than 1 bit/base
   - Similar to Rotation encoding (34): 
   - Has no homopolymers, and its encoding density is 1.58 bits/base
   - We will use software to generate the most biologically stable primers/payloads
3. Church encoding:
   - encoding density is 1 bit/base
4. Blawat encoding, Grass encoding, Fountain

## Decoding: 
Algorithm design:
1. Sequence the DNA bases (Illumina/Nanopore)
2. Remove primers and identify data-encoding bases using algorithm (remove sequences similar to a primer based on Levenshtein distance)
3. Simplify homonucleotide sequence into nucleotides
4. FASTQ analysis to identify most likely sequence

## Error Correction
- For future research: Error correction via algorithms (HEDGES, Hamming codes, etc.)
- Reconstructing the file from block-based semantic storage
- Coalesce data to a specific patch (e.g., if latest patch selected, only coalesce data from latest version)

