# Table of Contents
- [Stemming](#stemming)
- [Lemmatization](#lemmatization)
- [Tokenization](#tokenization)
  - [Types of Tokenization](#types-of-tokenization)
    - [Word Tokenization](#word-tokenization)
    - [Subword Tokenization](#subword-tokenization-detailed-explanation)
- [Word Tokenization](#word-tokenization)
- [Subword Tokenization](#subword-tokenization-detailed-explanation)
  - [Techniques for Subword Tokenization](#techniques-for-subword-tokenization)
    - [Byte Pair Encoding (BPE)](#byte-pair-encoding-bpe)
    - [WordPiece]
    - [SentencePiece]
- [Byte Pair Encoding (BPE)](#byte-pair-encoding-bpe)

---

### Stemming
Stemming is a text normalization technique used in natural language processing (NLP) to `reduce words to their root or base form`, known as the stem. This process helps in reducing the dimensionality of text data by treating different forms of a word as the same entity, which can improve the performance of text analysis and information retrieval systems.

#### Limitations
Over-stemming: When two words with different meanings are reduced to the same stem (e.g., "university" and "universe" might both stem to "univers").  
Under-stemming: When two words that should be reduced to the same stem are not (e.g., "alumnus" and "alumni" might not stem to the same root).

### Examples:
    "Running" → "Run"
    "Happiness" → "Happi"
    "Went" → "Wen"

### Lemmatization
Lemmatization is a text normalization technique used in natural language processing (NLP) to `reduce words to their base or dictionary form`, known as the lemma. `Unlike stemming`, which chops off word endings, `lemmatization considers the context and part of speech of a word` to derive its lemma, resulting in more accurate and meaningful base forms.

### Examples
    "Running" → "Run"
    "Happiness" → "Happy"
    "Went" → "Go"

### Tokenization
Tokenization is the process of breaking down text into smaller units called tokens, which can be words, subwords, or even individual characters. It's a crucial step in natural language processing (NLP) and machine learning, as it helps convert raw text into a format that algorithms can understand and process.

#### Types of Tokenization:

1. **Word-based Tokenization**:  
   This is the simplest form of tokenization, where text is split into individual words based on spaces or punctuation.  
   example  
   `The sentence "The quick brown fox jumps over the lazy dog" would be tokenized into: ["The", "quick", "brown", "fox", "jumps", "over", "the", "lazy", "dog"].`

2. **Subword Tokenization**:  
   Subword tokenization breaks down words into smaller units, which can be useful for handling out-of-vocabulary words and morphologically rich languages. 

    ##### **Two popular subword tokenization algorithms are**

    1. **Byte Pair Encoding (BPE)**: This algorithm starts with a vocabulary of individual characters and iteratively merges the most frequent pair of symbols until a desired vocabulary size is reached.
    2. **WordPiece**: Similar to BPE, WordPiece is used in models like BERT and starts with a vocabulary of individual characters, then iteratively adds the most frequent subword units.

3. **Character-based Tokenization**  
   In this approach, text is broken down into individual characters. This can be useful for languages with complex writing systems or when dealing with typos and misspellings. However, it can result in longer sequences and may not capture semantic meaning as effectively as word or subword tokenization.

4. **Other Techniques**  
   Rule-based Tokenization: Uses predefined rules to split text into tokens, often based on language-specific patterns or regular expressions.  
   Statistical Tokenization: Uses statistical models to determine the most likely token boundaries based on the context of the text.

   Tokenization techniques can significantly impact the performance of NLP models, and the choice of technique depends on the specific task, language, and available resources. As an AI model, I use a combination of these techniques to process and understand text input from users.

### Word Tokenization
Word tokenization is the process of breaking down a text into individual words or tokens. It is a fundamental step in natural language processing (NLP) and is used to convert raw text into a format that can be easily processed by algorithms.

#### Word tokenization typically involves the following steps:

- **Text Preprocessing**: The input text is cleaned and preprocessed to remove any unwanted characters, such as punctuation or special symbols, that may interfere with the tokenization process.
- **Splitting**: The preprocessed text is then split into individual words based on whitespace or other delimiters. This can be done using simple string manipulation techniques or more sophisticated algorithms.
- **Tokenization**: Each word is then treated as a separate token. In some cases, additional processing may be applied to handle contractions, hyphenated words, or other special cases.

#### Advantages of Word Tokenization
- **Simplicity**: Word tokenization is a straightforward process that is easy to implement and understand.
- **Interpretability**: The resulting tokens are human-readable and can be easily interpreted.
- **Efficiency**: Word tokenization can be performed quickly, making it suitable for processing large volumes of text.

#### Disadvantages of Word Tokenization
- **Out-of-Vocabulary (OOV) Words**: Word tokenization can struggle with words that are not present in the training data, leading to OOV issues.
- **Morphological Variations**: It may not handle morphological variations of words well, such as different forms of the same word (e.g., "run," "running," "ran").
- **Language Dependency**: Word tokenization can be language-dependent, requiring different rules for different languages.

#### Algorithms Using Word Tokenization

Word tokenization is used in various NLP algorithms and models, including:

- **Bag of Words (BoW)**: A simple representation of text that counts the frequency of each word in a document.
- **Term Frequency-Inverse Document Frequency (TF-IDF)**: A statistical measure used to evaluate the importance of a word in a document within a corpus.

#### Popular Word Tokenization Libraries and Tools
- **NLTK (Natural Language Toolkit)**: A popular Python library for NLP that includes various tokenization tools.
- **spaCy**: Another Python library for NLP that provides efficient and accurate tokenization.

### Subword Tokenization: Detailed Explanation
Subword tokenization is a technique used in natural language processing (NLP) to break down text into smaller units called subwords. Unlike word tokenization, which splits text into whole words, subword tokenization can split words into smaller meaningful units, such as prefixes, suffixes, or even individual characters. This approach is particularly useful for handling out-of-vocabulary (OOV) words, morphologically rich languages, and improving the efficiency of language models.

#### Subword tokenization typically involves the following steps:

- **Text Preprocessing**: Similar to word tokenization, the input text is cleaned and preprocessed to remove unwanted characters.

- **Vocabulary Building**: A vocabulary of subwords is created based on the training data. This vocabulary can be built using various algorithms, such as Byte Pair Encoding (BPE) or WordPiece.

- **Tokenization**: The preprocessed text is then tokenized into subwords based on the vocabulary. This can involve splitting words into smaller units or keeping them as whole words if they are present in the vocabulary.

#### Techniques for Subword Tokenization

1. **Byte Pair Encoding (BPE)**:

   - BPE starts with a vocabulary of individual characters and iteratively merges the most frequent pair of symbols until a desired vocabulary size is reached.
   - It is used in models like GPT-2 and RoBERTa.

2. **WordPiece**:

   - Similar to BPE, WordPiece is used in models like BERT and starts with a vocabulary of individual characters, then iteratively adds the most frequent subword units.
   - It can handle OOV words by breaking them down into known subwords.

3. **SentencePiece**:

   - SentencePiece is a language-independent subword tokenizer and detokenizer that can handle any language without the need for language-specific preprocessing.
   - It is used in models like ALBERT and T5.

#### Advantages of Subword Tokenization
- **Handling OOV Words**: Subword tokenization can effectively handle OOV words by breaking them down into known subwords.
- **Morphological Variations**: It can capture morphological variations of words, such as different forms of the same word.
- **Efficiency**: Subword tokenization can lead to more efficient language models by reducing the vocabulary size and improving the representation of words.

#### Disadvantages of Subword Tokenization
- **Complexity**: Subword tokenization can be more complex to implement and understand compared to word tokenization.
- **Language Dependency**: While less language-dependent than word tokenization, some subword tokenization techniques may still require language-specific tuning.
- **Interpretability**: The resulting subwords may be less interpretable than whole words, making it harder to understand the model's decisions.

#### Algorithms Using Subword Tokenization

Subword tokenization is used in various NLP algorithms and models, including:

- **Transformer-based Models**: Models like BERT, GPT-2, RoBERTa, ALBERT, and T5 use subword tokenization to improve their performance.
- **Neural Machine Translation (NMT)**: Subword tokenization is used in NMT systems to handle OOV words and improve translation quality.

### Byte Pair Encoding (BPE) 
[Reference Video](https://www.youtube.com/watch?v=fKd8s29e-l4)
Byte Pair Encoding (BPE) is a text compression and tokenization algorithm widely used in natural language processing (NLP), particularly for large language models like GPT, RoBERTa, and others. It was first introduced in 1994 by Philip Gage as a data compression technique and later adapted for NLP tasks.

#### Key Concepts of BPE
- **Vocabulary**: A set of subword units used to represent text.
- **Byte**: A unit of digital information, typically consisting of eight bits.
- **Character**: A symbol representing a written or printed letter or numeral.
- **Frequency**: The number of times a byte or character occurs in a text corpus.
- **Merge**: The process of combining two consecutive bytes or characters to create a new subword unit.

#### Working
BPE operates in two main phases: vocabulary construction and tokenization.

- **Vocabulary Construction**
  - **Initialization**: Start with a base vocabulary consisting of all unique characters in the text corpus.
  - **Tokenization at Character Level**: Each word in the corpus is initially represented as a sequence of characters.
  - **Counting Pair Frequencies**: Identify the most frequent adjacent pairs of tokens in the corpus.
  - **Merging the Most Frequent Pair**: Merge the most frequent pair into a new token and add it to the vocabulary.
  - **Recounting Pair Frequencies**: After each merge, recalculate the frequencies of the remaining pairs.
  - **Iterative Merging**: Repeat steps 4 and 5 until a predefined vocabulary size is reached.

#### Example:

Suppose we have a corpus with the words "low" and "lowest". The process would look like this:

- **Initialization**: Vocabulary = {l, o, w, e, s, t, }
- **Tokenization**: "low" -> l o w \</w>, "lowest" -> l o w e s t \</w>
- **Counting Pair Frequencies**: Pairs like l o, o w, w \</w>, e s, s t are counted.
- **Merging the Most Frequent Pair**: If o w is the most frequent, merge it to form ow. Vocabulary becomes {l, o, w, e, s, t, , ow}.
- **Recounting Pair Frequencies**: Recalculate frequencies with the new token ow.
- **Iterative Merging**: Continue merging until the desired vocabulary size is reached, e.g., merging l ow to form low, then e s to form es, and finally es t to form est.

The final vocabulary might be {low, est, }, representing "low" as low \</w> and "lowest" as low est \</w>.

#### Tokenization

Once the vocabulary is constructed, BPE tokenizes new text by applying the learned merge rules in the order they were learned. This process breaks down the text into subword units from the vocabulary.

- **Pre-tokenization**: Split the new text into words and append an end-of-word symbol (e.g., \</w>).
- **Apply Merge Rules**: Start with the character-level representation and apply the merge rules iteratively until no more merges are possible.

#### Example:

For the new text "newest binded lowers", the tokenization process would be:

- **Pre-tokenization**: "newest binded lowers" -> newest\</w> binded\</w> lowers\</w>
- **Character-level Representation**: n e w e s t \</w> b i n d e d \</w> l o w e r s \</w>
- **Applying Merge Rules**: Using the vocabulary {low, est, }, the text would be tokenized as [n, e, w, est, \</w>, [UNK], i, n, d, e, d, \</w>, low, e, r, s, \</w>].

#### Advantages of BPE
- **Efficient Vocabulary Size**: BPE balances vocabulary size and sequence length, reducing the number of tokens needed to represent text.
- **Handling Out-of-Vocabulary Words**: It can represent rare or new words using subword units, improving model flexibility.
- **Context-Aware Tokenization**: BPE captures linguistic patterns like common prefixes, suffixes, and word stems.

#### Limitations of BPE
- **Fixed Vocabulary Size**: The vocabulary size is predetermined, which can lead to over-segmentation if too small or unnecessary subword units if too large.

#### Popular Algorithems uses this BPE
- GPT (Generative Pre-trained Transformer)
- RoBERTa
- BART (Bidirectional and Auto-Regressive Transformer)
- DeBERTa
- LLaMA

# WordPiece


> [!NOTE]  
> Useful References.  
> [Reference Video of BPE](https://www.youtube.com/watch?v=fKd8s29e-l4)