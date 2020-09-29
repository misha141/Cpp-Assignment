# Cpp-Assignment

## Question 1

John is very good at writing algorithms. At his university, he is given a problem to solve in which he is given a dictionary(eg. set of 10 lakh words). And he will be given some inputs to check whether those inputs exist in the dictionary or not ? John is a memory efficient guy so he tries to solve every problem in the most efficient way he
could do. So here is how he approaches the problem. John knows that serialising the given data would reduce the size of data a lot and then he’ll be
able to load the data onto RAM. So what John wants to do is to read all the data from the dictionary, make a Trie and serialize it. Then load that serialized Trie on RAM and perform traversal operation on that serialized data. John is stuck in this problem and wants you to help him with his approach. Below are the inputs provided by John.

Input :

1. A sample dictionary* file with words and their frequency.

2. Few example inputs below.


Output :

1. YES if the word exists and it’s frequency.

2. NO if the word doesn’t exist in the given dictionary.


Example:

INPUT : Keyboard

OUTPUT : YES, 139

INPUT : Rahul

OUTPUT : No

### Solution:
```
#include <bits/stdc++.h> 
using namespace std; 
  
// Structure for Trie 
struct Trie { 
    bool isEndOfWord; 
    unordered_map<char, Trie*> map; 
     
}; 
  
Trie* getNewTrieNode() 
{ 
    Trie* node = new Trie; 
    node->isEndOfWord = false; 
    return node; 
} 
  
void insert(Trie*& root, const string& str) 
{ 
  
    // If root is null 
    if (root == NULL) 
        root = getNewTrieNode(); 
  
    Trie* temp = root; 
    for (int i = 0; i < str.length(); i++) { 
        char x = str[i]; 
  
        // Make a new node if there is no path 
        if (temp->map.find(x) == temp->map.end()) 
            temp->map[x] = getNewTrieNode(); 
  
        temp = temp->map[x]; 
    } 
  
    // Mark end of word and store the meaning 
    temp->isEndOfWord = true;  
} 
  
// Function to search a word in the Trie and its frequency
int getCount(Trie* root, const string& word) 
{
    int count=0; 
    // If root is null i.e. the dictionary is empty 
    if (root == NULL) 
        return ""; 
  
    Trie* temp = root; 
  
    // Search a word in the Trie 
    for (int i = 0; i < word.length(); i++) { 
        temp = temp->map[word[i]]; 
        if (temp == NULL) 
            return ""; 
    } 
  
    // If it is the end of a valid word stored 
    // before then return its meaning 
    if (temp->isEndOfWord) 
        return count++;
    return ""; 
} 
  
// Driver code 
int main() 
{ 
    Trie* root = NULL; 
  
    // Build the dictionary 
    insert(root, "language”); 
    insert(root, "computer”); 
    insert(root, "map”);
    insert(root, "book”); 
    insert(root, "science”);
 
  
    string str = "map"; 
    cout << getCount(root, str); 
  
    return 0; 
} 

```

## Question 2

Given a dictionary. Make a Trie out of that dictionary and mark each end node with numbers
starting from 0 to N, where N should be equal to the total number of words in the dictionary.
Now you will be given input from 0 to N. You have to backtrace that node and find the exact
word ending at that node.

### Solution

```
#include <bits/stdc++.h> 
using namespace std; 
  
const int ALPHABET_SIZE = 26; 
  
// trie node 
struct TrieNode 
{ 
    struct TrieNode *children[ALPHABET_SIZE];
    bool isEndOfWord; 
}; 
  
 
struct TrieNode *getNode(void) 
{ 
    struct TrieNode *pNode =  new TrieNode; 
  
    pNode->isEndOfWord = false; 
  
    for (int i = 0; i < ALPHABET_SIZE; i++) 
        pNode->children[i] = NULL; 
  
    return pNode; 
} 
  
void insert(struct TrieNode *root, string key) 
{ 
    struct TrieNode *pCrawl = root; 
  
    for (int i = 0; i < key.length(); i++) 
    { 
        int index = key[i] - 'a'; 
        if (!pCrawl->children[index]) 
            pCrawl->children[index] = getNode(); 
  
        pCrawl = pCrawl->children[index]; 
    } 
  
    // mark last node as leaf 
    pCrawl->isEndOfWord = true; 
} 
  
// Returns true if key presents in trie, else 
// false 
bool traverse(struct TrieNode *root) 
{ 
    struct TrieNode *pCrawl = root; 
  
    for (int i = 0; i < key.length(); i++) 
    { 
        int index = key[i] - 'a'; 
        if (!pCrawl->children[index]) 
            return false; 
  
        pCrawl = pCrawl->children[index]; 
    } 
  
    return index; 
} 
  
// Driver 
int main() 
{ 
    // Input keys (use only 'a' through 'z' 
    // and lower case) 
    string keys[] = {"the", "a", "there", 
                    "answer", "any", "by", 
                     "bye", "their" }; 
    int n = sizeof(keys)/sizeof(keys[0]); 
  
    struct TrieNode *root = getNode(); 
    cout<<traversal;
    return 0; 
} 
```
