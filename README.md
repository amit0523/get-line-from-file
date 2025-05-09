File get_line_from_file.c implements a function get_line_from_file() which is an
alternate implementation of C library's getline() function and this function is
simpler to use than getline().

Function get_line_from_file() returns a line from the file represented by fd.

This function supports only regular files (no pipes, sockets, etc).

If fd is less than 0 then NULL is returned and *error_num is assigned the
appropriate error value (INVALID_FD in this case).

In case of any error, *error_num is assigned the appropriate error value.

The high level algorithm of this function is:

    The function get_line_from_file() reads some bytes in a buffer from the file
    and tries to find the newline in the buffer. If the newline is not found
    then it reads more bytes from the file in the buffer. When the newline is
    found in the buffer, then the newline is replaced with the null terminating
    character and the buffer is reallocated to the correct size. Then the file
    offset for reading is set to the start of the next line. And then the buffer
    is returned to the user.

Please note that the returned line/buffer doesn't contain any newlines.

The line/buffer returned by this function is allocated using realloc(), so it is
user's responsibility to free the line (free memory).

---- End of README ----
