# LZ77_cetsat

Terminologies
1.Coding point=location of the byte currently being inspected
2.Window= buffer

output format
<offset,length of match, codeword>

Working:
It works as follows: bytes are read in a sequence from first to last, the location of the byte currently being inspected is known as the 'coding point'. Each byte at the coding point is compared to information preceding it, in a buffer known as a 'window', this window would not be expected to match the whole size of the data, but it may extend to more than a few thousand bytes. If one, or many bytes within this window match the sequence currently located at the coding point, then a pointer is saved to the compressed data. This pointer consists of an offset from the current coding point to the repeated data, and how many bytes have been matched. This value is subsequently described as the pointer's 'length'. When the pointer is recorded, the byte immediately after the matched sequence at the coding point is also stored. If no match was found within the window, which would always happen when the first element is read from a file, then a null pointer is saved along with the byte at the coding point is saved with it. So whether we find a match in our window or not, we always save a pointer alongside a single byte as we work our way through the data.
