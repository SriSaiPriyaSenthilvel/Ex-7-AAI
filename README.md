<H3>ENTER YOUR NAME : SRI SAI PRIYA S</H3>
<H3>ENTER YOUR REGISTER NO. : 212222240103</H3>
<H3>EX. NO.7</H3>
<H3>DATE:</H3>
<H1 ALIGN =CENTER>Implementation of Text  Summarization</H1>

# Aim:
to perform automatic text summarization using Natural Language Processing (NLP) techniques. 
 <BR>
 
# Algorithm:
Step 1 Import necessary libraries for natural language processing tasks.<BR>
Step 2: Download NLTK resources, including the punkt tokenizer and stopwords.<BR>
Step 3: Define Text Preprocessing Function to tokenize, remove stopwords, and perform stemming.<BR>
Step 4: Define the Text Summarization Function using a simple frequency-based approach.<br>
    - Calculate the frequency of each word in the preprocessed text.<br>
    - Calculate a score for each sentence based on the sum of word frequencies.<br>
    - Select the top N sentences with the highest scores to form the summary.<br>
Step 5: Construct the main program to read the paragraph  and perform text summarization<br>
      - Generate and print the original text.<br>
      - Generate and print the text summary using the  Text Summarization function<br>

# Program:

```
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize,sent_tokenize
from nltk.stem import PorterStemmer
nltk.download( 'punkt' )
nltk.download( 'stopwords' )

def preprocess_text(text):

 # Tokenize the text into words
	words = word_tokenize(text)

 # Remove stopwords and punctuation
	Swords= set(stopwords.words('english'))
	Fwords=[w for w in words if w.lower()not in Swords and w.isalnum()]

 # Stemming
	stemmer = PorterStemmer()
	SMwords= [stemmer.stem(word) for words in Fwords]
	return SMwords

 def generate_summary(text,num_sentences=3):
	S= sent_tokenize(text)
	PreText = preprocess_text(text)

 # Calculate the frequency of each word
	WordFre=nltk.FreqDist(PreText)

 # Calculate the score for each sentence based on word frequency
	scores={}
	for i in S:
		for word,freq in WordFre.items():
			if word in i.lower():
				if i not in scores:
					scores[i]=freq
				else:
					scores[i]+= freq

# Select top N sentences with highest scores
	summary=sorted(scores,key=scores.get,reverse=True)[:num_sentences]

	return ' '. join(summary)

 if __name__=="__main__":
	input_text ="""
Artificial intelligence is revolutionizing various fields by enhancing efficiency and creativity.
From automating mundane tasks to generating art and music, AI is reshaping our daily lives. 
Its ability to analyze vast amounts of data enables smarter decision-making in industries. 
However,as we embrace these advancements,ethical considerations and responsible usage become crucial. 
Balancing innovation with accountability will determine the future impact of AI on society."""

summary = generate_summary(input_text)
print("Origina1 Text: ")
print (input_text )
print( " \nSummary : " )
print(summary)
```

# Output:

![image](https://github.com/user-attachments/assets/8e0448b4-f21b-4f13-b115-6f60dd2a97d9)

# Result:
Thus ,the program to perform the Text summarization is executed sucessfully.


