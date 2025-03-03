# Teknik-Kompilasi
# Materi Teknik Kompilasi (14 Pertemuan)

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

## **Pertemuan 4 - 6: Teknik Top Downparsing dengan recursive descent parser dan LL(1)
- Teknik Top-Down Parsing adalah metode parsing yang membangun pohon sintaksis mulai dari simbol awal (start symbol)
- Secara bertahap menguraikan aturan produksi menuju terminal. Dua teknik utama dalam Top-Down Parsing adalah Recursive Descent Parser dan LL(1) Parser.

## **Pertemuan 7 (E-learning)

## **Pertemuan 8 - 9: Teknik Bottom-up Parsing dengan LR (0), SLR (1), LR(1), LALR(1)
- Bottom-Up Parsing adalah teknik parsing yang membangun pohon sintaksis dari daun (token) ke akar (start symbol) dengan melakukan reduksi terhadap aturan grammar.

## **Pertemuan 10 : Proses Kerja one pass compiler
- One-pass compiler adalah kompilator yang menerjemahkan kode sumber ke dalam kode mesin dalam satu lintasan (single pass) tanpa kembali ke bagian kode sebelumnya.

## **Pertemuan 11 : Membuat Translator Scheme dengan bahasa semantik dan translator scheme


## **Pertemuan 12 : Membangun Intermediate Code dan Mengelola Tabel Simbol

## **Pertemuan 13 : Membuat Optimasi Parser Linier Optimazation

## **Pertemuan 14 (E-Learning)






