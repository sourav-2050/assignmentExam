# MatrixKey SubShift Cipher

### Course Info

- **Course Title:** Mathematical Analysis for Computer Science
- **Course Code:** CSE 361

### Submitted By

- **Name:** Md. Sihabur Islam Sourav
- **Student ID:** 2102013

### Submitted To

- **Instructor:** Pankaj Bhowmik

Lecturer, Department of CSE

---

## 🔐 Algorithm Title: MatrixKey SubShift Cipher

A block-based symmetric cipher that uses a numeric matrix as a key to control substitution and positional shifting within blocks of characters.

---

## 🧩 Algorithm Description

### 🔸 Key

A square matrix of size *n x n*, used to guide shifting operations.

**Example Key Matrix (2x2):**

```
[2, 3]
[1, 4]
```

### 🔸 Encryption Steps

1. Convert the plaintext into ASCII.
2. Divide the text into blocks of *n* characters.
3. For each character `i` in a block:
   - Apply shift: `ASCII(char) + matrix[i][i]` mod 128.
   - Append the resulting character to ciphertext.

### 🔸 Decryption Steps

1. Divide the ciphertext into blocks of size *n*.
2. For each character `i` in a block:
   - Subtract the corresponding `matrix[i][i]` from the ASCII code.
   - Convert back to character.

---

## 🧪 Example Test Case

### Input:

- **Plaintext**: `ABCD`
- **Matrix (2x2)**:

```
[2, 3]
[1, 4]
```

### Encryption:

| Char | ASCII | Shift | Result |
| ---- | ----- | ----- | ------ |
| A    | 65    | +2    | 67 → C |
| B    | 66    | +4    | 70 → F |
| C    | 67    | +2    | 69 → E |
| D    | 68    | +4    | 72 → H |

**Ciphertext: `CFEH`**

### Decryption:

| Char | ASCII | Shift | Result |
| ---- | ----- | ----- | ------ |
| C    | 67    | -2    | 65 → A |
| F    | 70    | -4    | 66 → B |
| E    | 69    | -2    | 67 → C |
| H    | 72    | -4    | 68 → D |

**Recovered Plaintext: `ABCD`**

---

## 🔣 Pseudocode

### Encryption

```text
ENCRYPT(text, key_matrix):
    n = len(key_matrix)
    cipher = ""
    for block in split(text, n):
        for i in range(len(block)):
            code = ord(block[i])
            code = (code + key_matrix[i][i]) % 128
            cipher += chr(code)
    return cipher
```

### Decryption

```text
DECRYPT(cipher, key_matrix):
    n = len(key_matrix)
    text = ""
    for block in split(cipher, n):
        for i in range(len(block)):
            code = ord(block[i])
            code = (code - key_matrix[i][i]) % 128
            text += chr(code)
    return text
```

---

## 💻 Source Code (Python)

```python
def encrypt(text, key):
    n = len(key)
    cipher = ""
    for i in range(0, len(text), n):
        block = text[i:i+n]
        for j in range(len(block)):
            code = ord(block[j])
            code = (code + key[j][j]) % 128
            cipher += chr(code)
    return cipher

def decrypt(cipher, key):
    n = len(key)
    text = ""
    for i in range(0, len(cipher), n):
        block = cipher[i:i+n]
        for j in range(len(block)):
            code = ord(block[j])
            code = (code - key[j][j]) % 128
            text += chr(code)
    return text

# Example usage
key = [[2,3],[1,4]]
msg = "ABCD"
encrypted = encrypt(msg, key)
decrypted = decrypt(encrypted, key)

print("Plaintext:", msg)
print("Encrypted:", encrypted)
print("Decrypted:", decrypted)
```

---

## 📊 Flowchart
<img width="1024" height="1536" alt="Image" src="https://github.com/user-attachments/assets/3a40a30c-87db-40ec-ad9d-c60a7de8425f" />


---

## 📁 Submission Notes

- Upload this file as `README.md` in a GitHub repository.
- Add `main.py` with the source code.
- Include `flowchart.png`.
- Mention course and student details.

---

**End of Report** ✅
