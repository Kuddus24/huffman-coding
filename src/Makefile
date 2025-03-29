CC = gcc
CFLAGS = -Wall -Wextra
SRCS = src/huffman_encoder.c src/huffman_decoder.c
BINS = huffman_encoder huffman_decoder

all: $(BINS)

huffman_encoder: src/huffman_encoder.c
	$(CC) $(CFLAGS) -o $@ $<

huffman_decoder: src/huffman_decoder.c
	$(CC) $(CFLAGS) -o $@ $<

clean:
	rm -f $(BINS)

.PHONY: all clean
