# Computational Theory

A comprehensive educational implementation of the SHA-256 cryptographic hash function from first principles, including a complete password security assessment framework. This project demonstrates both the mathematical foundations of cryptographic hash functions and their practical applications in cybersecurity.

## 🎯 Project Overview

This repository implements **SHA-256 from scratch** following the official [**FIPS 180-4 specification**](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf) (the authoritative U.S. government standard defining SHA-256's mathematical operations, constants, and test vectors), progressing through five interconnected problems that build a complete cryptographic system:

1. **Cryptographic Auxiliary Functions** - Core SHA-256 bit manipulation operations
2. **Round Constants Generation** - Mathematical derivation from prime numbers
3. **Message Parsing & Preprocessing** - Block formatting and padding
4. **SHA-256 Hash Function** - Complete implementation and verification
5. **Password Security Assessment** - Real-world cryptographic applications

### 🔒 Key Features

- ✅ **FIPS 180-4 Compliant**: Bit-perfect implementation matching official test vectors
- ✅ **Educational Focus**: Comprehensive explanations of cryptographic mathematics
- ✅ **Security Analysis**: Practical password security assessment framework
- ✅ **Production Quality**: Detailed documentation and verification testing
- ✅ **Interactive Learning**: Jupyter notebook with step-by-step explanations

## 🚀 Quick Start

### Prerequisites

- **[Python](https://www.python.org/) 3.7+** - Programming language for cryptographic implementation. Version 3.7+ required for f-string support and consistent integer arithmetic behavior across platforms
- **[Jupyter Notebook](https://jupyter.org/)** - Interactive computing environment that allows you to view, edit, and execute the educational content with live code, mathematical equations, and explanatory text
- **Required packages** listed in `requirements.txt` (automatically installed in next step)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/haroldlaw/Computational-Theory.git
   cd Computational-Theory
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Launch Jupyter notebook:**
   ```bash
   jupyter notebook problems.ipynb
   ```
   
   Or for JupyterLab:
   ```bash
   jupyter lab problems.ipynb
   ```

### Quick Verification

Test the complete SHA-256 implementation:

```python
# Execute in Jupyter notebook or Python shell
from problems import *  # Import all implemented functions

# Test against official NIST test vector
message = "abc"
expected = "ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f20015ad"
result = sha256_complete(message.encode()).hex()

assert result == expected, f"Expected {expected}, got {result}"
print("✅ SHA-256 implementation verified!")
```

## 📚 Project Structure

### Problem 1: Cryptographic Auxiliary Functions
Implementation of core SHA-256 bit manipulation operations:

- **`parity(x, y, z)`** - Three-way XOR operation with cryptographic analysis
- **`ch(x, y, z)`** - Choice function for conditional bit selection  
- **`maj(x, y, z)`** - Majority function for consensus-based operations
- **`rotr(x, n)`** - Right rotation (information-preserving)
- **`shr(x, n)`** - Right shift (information-destroying)
- **`sigma0(x), sigma1(x)`** - Message schedule functions (lowercase σ)
- **`Sigma0(x), Sigma1(x)`** - Compression functions (uppercase Σ)

### Problem 2: Round Constants Generation
Mathematical derivation of SHA-256's 64 round constants:

- **`primes(n)`** - Sieve of Eratosthenes for prime generation
- **`extract_fractional_bits(x)`** - [**IEEE 754**](https://ieeexplore.ieee.org/document/4610935) compliant fractional bit extraction for converting irrational cube roots to deterministic 32-bit constants
- **`calculate_sha256_constants()`** - Complete constant generation pipeline

**Mathematical Foundation:** `K[i] = floor(frac(∛pᵢ) × 2³²)` where pᵢ is the ith prime

### Problem 3: Message Parsing & Preprocessing
FIPS 180-4 compliant message formatting:

- **`block_parse(message)`** - Multi-block preprocessing with proper padding
- **Message length encoding** - 64-bit big-endian length representation
- **512-bit block alignment** - Ensures compatibility with compression function

### Problem 4: Complete SHA-256 Implementation
Full hash function with verification:

- **`hash(message_block, constants)`** - Single block compression
- **`sha256_complete(message)`** - Complete multi-block hash function
- **Official test vector validation** - NIST compliance verification

### Problem 5: Password Security Assessment
Real-world cryptographic security analysis:

- **`build_attack_dictionaries()`** - Comprehensive password attack vectors
- **`execute_dictionary_attack()`** - Multi-phase dictionary attacks
- **`execute_brute_force_attack()`** - Computational brute force simulation
- **`analyze_results()`** - Quantitative security assessment
- **`demonstrate_secure_hashing()`** - Secure vs. insecure hashing comparison

## 🔐 Password Security Features

### Attack Simulation Framework
- **Dictionary attacks** with 10,000+ password variations
- **Brute force analysis** with computational complexity assessment
- **Security metrics** following [**NIST cybersecurity framework**](https://www.nist.gov/cyberframework) and [**OWASP testing standards**](https://owasp.org/www-project-web-security-testing-guide/)
- **Risk assessment** with business impact analysis

### Secure Hashing Demonstration
- **PBKDF2-SHA256** with configurable iteration counts following [**NIST SP 800-132**](https://csrc.nist.gov/publications/detail/sp/800-132/final) password-based key derivation guidelines
- **Argon2id** integration for memory-hard key derivation per [**RFC 9106**](https://tools.ietf.org/html/rfc9106) specification
- **Attack economics** analysis for threat modeling
- **Implementation guidance** for production security

## 📖 Educational Content

Each function includes comprehensive documentation covering:

- **Mathematical foundations** with formal definitions
- **Cryptographic properties** and security analysis
- **Implementation details** with optimization strategies
- **Historical context** and design rationale
- **Real-world applications** and security implications

### Cryptographic Concepts Covered

- **Boolean functions** in cryptographic design
- **Avalanche effect** and bit diffusion principles
- **Information theory** applications in hash functions
- **Attack resistance** against differential/linear cryptanalysis
- **"Nothing-up-my-sleeve" numbers** for transparent security

## 🛡️ Security Applications

### Password Policy Development
- Quantitative strength assessment
- Business risk evaluation
- Compliance framework alignment
- Implementation timeline guidance

### Cryptographic Best Practices
- Secure password storage implementation
- Hash function selection criteria
- Performance vs. security trade-offs
- Migration strategies for legacy systems

## 🧪 Testing & Verification

### Official Test Vectors
All implementations validated against:
- [**NIST SHA-256 test vectors**](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/secure-hashing) for algorithmic correctness
- [**FIPS 180-4 specification**](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf) compliance for bit-perfect implementation
- Cross-platform consistency verification
- Edge case and boundary condition testing

### Performance Benchmarks
- Computational complexity analysis
- Memory usage optimization
- Hardware implementation considerations
- Scalability assessment

## 📋 Requirements

### Core Dependencies
- **[NumPy](https://numpy.org/)** (≥1.19.0) - Essential for precise 32-bit unsigned integer arithmetic required by SHA-256. Provides `np.uint32` type ensuring consistent modular arithmetic across different platforms and preventing integer overflow issues
- **[Jupyter](https://jupyter.org/)** (≥1.0.0) - Interactive notebook environment enabling step-by-step execution and visualization of cryptographic algorithms with embedded explanations

### Optional Dependencies
- **[JupyterLab](https://jupyterlab.readthedocs.io/)** (≥3.0.0) - Next-generation web-based interface for Jupyter notebooks, offering improved file browser, integrated terminal, and enhanced debugging capabilities
- **[argon2-cffi](https://github.com/hynek/argon2-cffi)** - Python bindings for the Argon2 password hashing library, winner of the Password Hashing Competition. Required for demonstrating state-of-the-art secure password storage in Problem 5

### Standard Library
- **[math](https://docs.python.org/3/library/math.html)** - Mathematical operations including `floor()` for fractional bit extraction and `sqrt()` for prime generation algorithms
- **[time](https://docs.python.org/3/library/time.html)** - High-precision timing for performance benchmarks and attack simulation timing analysis
- **[hashlib](https://docs.python.org/3/library/hashlib.html)** - Built-in cryptographic hash functions for verification against standard library implementations and PBKDF2 demonstrations
- **[string](https://docs.python.org/3/library/string.html), [itertools](https://docs.python.org/3/library/itertools.html)** - Character set definitions and combinatorial functions for systematic password enumeration in security assessments

## 🤝 Contributing

This educational project welcomes contributions that enhance:
- Mathematical explanations and correctness
- Security analysis depth and accuracy  
- Code documentation and clarity
- Performance optimization strategies
- Additional cryptographic examples

## 📜 License

This project is provided for **educational purposes** under standard academic use guidelines. The SHA-256 algorithm itself is a public domain specification published by NIST.

## 🔗 References

- [FIPS 180-4: Secure Hash Standard](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)
- [NIST SP 800-132: Password-Based Key Derivation](https://csrc.nist.gov/publications/detail/sp/800-132/final)
- [OWASP Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)
- [IEEE 754-2008 Floating Point Standard](https://ieeexplore.ieee.org/document/4610935)

## 🎓 Educational Impact

This implementation serves as a **complete educational resource** for understanding:
- Cryptographic hash function design principles
- Mathematical foundations of digital security
- Practical cybersecurity assessment techniques
- Industry-standard cryptographic implementations

Perfect for **computer science students**, **cybersecurity professionals**, and **anyone seeking deep understanding** of cryptographic systems that protect our digital world.

---

**⚡ Ready to explore cryptographic security? Start with `jupyter notebook problems.ipynb` and begin your journey through the mathematical foundations of digital security!**