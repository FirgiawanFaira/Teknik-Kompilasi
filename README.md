# Teknik-Kompilasi
# Materi Teknik Kompilasi dengan Python (14 Pertemuan)

## **Pertemuan 1: Pendahuluan Teknik Kompilasi**
- Definisi kompilasi dan interpreter
- Perbedaan antara compiler dan interpreter
- Struktur umum dari sebuah compiler
- **Contoh:** Program sederhana dengan Python yang mendemonstrasikan interpretasi dan kompilasi menggunakan `exec()`

## **Pertemuan 2: Analisis Leksikal**
- Konsep token, lexer, dan scanner
- Finite State Automata (FSA) dalam analisis leksikal
- **Contoh:** Implementasi lexer sederhana menggunakan pustaka `re` dan `ply.lex`

```python
import ply.lex as lex

# Daftar token
tokens = ('NUMBER', 'PLUS', 'MINUS', 'TIMES', 'DIVIDE', 'LPAREN', 'RPAREN')

t_literale = {'+': 'PLUS', '-': 'MINUS', '*': 'TIMES', '/': 'DIVIDE', '(': 'LPAREN', ')': 'RPAREN'}

def t_NUMBER(t):
    r'\d+'
    t.value = int(t.value)
    return t

def t_error(t):
    print("Karakter ilegal!", t.value[0])
    t.lexer.skip(1)

lexer = lex.lex()
lexer.input("3 + 5 * (10 - 2)")
for tok in lexer:
    print(tok)
```

## **Pertemuan 3: Analisis Sintaksis (Parsing)**
- Konsep parse tree dan derivasi
- Penggunaan parser berbasis aturan (Context-Free Grammar)
- **Contoh:** Implementasi parser menggunakan `ply.yacc`

```python
import ply.yacc as yacc

# Aturan Grammar
precedence = (('left', 'PLUS', 'MINUS'), ('left', 'TIMES', 'DIVIDE'))

def p_expression_binop(p):
    '''expression : expression PLUS expression
                  | expression MINUS expression
                  | expression TIMES expression
                  | expression DIVIDE expression'''
    p[0] = (p[2], p[1], p[3])

def p_expression_number(p):
    'expression : NUMBER'
    p[0] = p[1]

def p_error(p):
    print("Syntax error!")

parser = yacc.yacc()
result = parser.parse("3 + 5 * 2")
print(result)
```

## **Pertemuan 4: Pembuatan AST (Abstract Syntax Tree)**
- Konsep AST dan manfaatnya
- **Contoh:** Pembuatan AST dengan `ast` module Python

## **Pertemuan 5: Analisis Semantik**
- Tipe data dan pengecekan tipe
- Scope dan binding
- **Contoh:** Implementasi tabel simbol menggunakan dictionary

## **Pertemuan 6: Intermediate Representation (IR)**
- Three Address Code (TAC)
- **Contoh:** Konversi ekspresi ke TAC

## **Pertemuan 7: Optimasi Kode**
- Optimasi pada IR (Dead Code Elimination, Constant Folding)
- **Contoh:** Implementasi optimasi sederhana di Python

## **Pertemuan 8: Generasi Kode**
- Pengenalan LLVM dan bytecode
- **Contoh:** Menggunakan `llvmlite` untuk menghasilkan bytecode

## **Pertemuan 9: Implementasi Backend Kompiler**
- Translasi IR ke assembly sederhana
- **Contoh:** Menulis file `.asm` dari Python

## **Pertemuan 10: Pembuatan Interpreter**
- Implementasi interpreter berbasis AST
- **Contoh:** Evaluasi AST dalam Python

## **Pertemuan 11: Analisis dan Debugging Kompiler**
- Teknik debugging dalam pembuatan kompiler
- **Contoh:** Logging dan visualisasi parse tree

## **Pertemuan 12: Studi Kasus Kompiler Python**
- Menelusuri bagaimana Python mengompilasi kode
- **Contoh:** Melihat bytecode menggunakan `dis` module

## **Pertemuan 13: Ujian Praktek**
- Implementasi mini-compiler dari awal

## **Pertemuan 14: Presentasi Proyek Akhir**
- Mahasiswa mempresentasikan mini-compiler mereka

---
Dokumen ini memberikan struktur lengkap untuk kuliah **Teknik Kompilasi** dengan Python. Tiap pertemuan mencakup konsep dan implementasi langsung agar lebih aplikatif.

