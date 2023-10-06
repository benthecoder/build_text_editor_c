# Build your own text editor

Following this guide: https://viewsourcecode.org/snaptoken/kilo/index.html

Code: https://github.com/snaptoken/kilo-src

## Notes

### Oct 6, 2023: setup and running and compiling C

- `main()` function is the default starting point
- C is a complied language, we run our program through a C compiler to turn it into an executable, then run that executable like we would any other program

```bash
cc kilo.c -o kilo
```

This creates an executable file

to run Kilo

```bash
./kilo
```

with make file

```bash
make kilo
```

In the make file

```makefile
kilo: kilo.c
    $(CC) kilo.c -o kilo -Wall -Wextra -pedantic -std=c99
```

- `-Wall` means all warnings, could get warnings that are bad practices of C
- `-Wextra` and `-pedantic` turn on more warnings. (only "unused variables" warnings, other warnings should be checked)
- `-std=c99` specifies the exact version of C language standard, which is [C99](https://en.wikipedia.org/wiki/C99) in this case. C99 allows declaration of variable anywhere in functions whereas ANSI C requires variables on top of a function block.

Errors faced

```txt
kilo.c:1:9: warning: a function declaration without a prototype is deprecated in all versions of C [-Wstrict-prototypes]
int main() {
        ^
         void
1 warning generated.
```

Fix: add void

```c
int main(void) {
    ...
```
