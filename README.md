# Huffman Coding Implementation

A C implementation of Huffman coding algorithm for text file compression and decompression.

## Overview

This project provides a complete implementation of the Huffman coding algorithm, consisting of:

1. **Huffman Encoder** - Compresses text files by generating variable-length codes based on character frequencies
2. **Huffman Decoder** - Decompresses the encoded files back to their original form

Huffman coding is a lossless data compression algorithm that assigns variable-length codes to input characters based on their frequencies. The most frequent characters are assigned the shortest codes, resulting in efficient compression.

## Features

- Generates frequency tables for input text files
- Builds a Huffman tree based on character frequencies
- Compresses text files with optimal bit-length encoding
- Decompresses encoded files with the help of frequency tables
- Displays compression statistics including compression ratio
- Provides a code table showing the Huffman codes for each character

## File Structure

```
huffman-coding/
├── src/
│   ├── huffman_encoder.c - Source code for the encoder
│   ├── huffman_decoder.c - Source code for the decoder
│   └── Makefile
├── include/
│   └── huffman.h - Header file (optional, for organization)
├── examples/
│   └── sample.txt - Sample text file for testing
└── README.md
```

## How to Compile

```bash
# Clone the repository
git clone https://github.com/yourusername/huffman-coding.git
cd huffman-coding

# Compile the programs
make
```

Or compile manually:

```bash
gcc -o huffman_encoder src/huffman_encoder.c
gcc -o huffman_decoder src/huffman_decoder.c
```

## Usage

### Encoding
```bash
./huffman_encoder <filename>
```
or without arguments to be prompted for the filename:
```bash
./huffman_encoder
```

The encoder will:
1. Read the input file
2. Generate a frequency table
3. Build a Huffman tree
4. Create and display a code table
5. Encode the file
6. Save the encoded file as `<filename>.huffman`
7. Save the frequency table as `<filename>.huffman.table`
8. Display compression statistics

### Decoding
```bash
./huffman_decoder <filename.huffman>
```
or without arguments to be prompted for the filename:
```bash
./huffman_decoder
```

The decoder will:
1. Read the encoded file
2. Read the frequency table
3. Rebuild the Huffman tree
4. Decode the file
5. Save the decoded file in a new directory: `<filename>.decoded/`

## How It Works

### Encoder Process

1. **Frequency Analysis**: The encoder reads the input file character by character and counts the frequency of each character.
2. **Priority Queue**: Characters are inserted into a priority queue based on their frequencies.
3. **Huffman Tree Construction**: The two nodes with the lowest frequencies are repeatedly removed and combined into a new internal node until only one node (the root) remains.
4. **Code Generation**: Traversing the Huffman tree, codes are assigned to each character (0 for left branches, 1 for right branches).
5. **File Encoding**: The original file is read again, and each character is replaced with its Huffman code. The encoded bits are packed into bytes and written to the output file.
6. **Table Storage**: The frequency table is saved to a separate file to be used during decoding.

### Decoder Process

1. **Table Reading**: The decoder reads the frequency table from the `.table` file.
2. **Tree Reconstruction**: The Huffman tree is reconstructed using the frequency information.
3. **Bit Stream Processing**: The encoded file is read bit by bit, traversing the Huffman tree (left for 0, right for 1) until reaching a leaf node.
4. **Character Output**: When a leaf node is reached, the corresponding character is output and tree traversal starts again from the root.

## Limitations

- The current implementation is designed for text files.
- The code handles ASCII characters (0-127).
- Very large files might require additional memory management.

## Future Improvements

- Add support for binary files and extended character sets
- Implement more efficient memory management for large files
- Create a unified program with both encoding and decoding functionality
- Add command line options for customization (e.g., output path)
- Implement multi-threading for improved performance on large files

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- This implementation is based on the classic Huffman coding algorithm described by David A. Huffman in 1952.
