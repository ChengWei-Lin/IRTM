# 107-1-IRTM
NTU 107-1 Information Retrieval and Text Mining

### HW1: Write a program to extract terms from a document.  
    1. Tokenization.
    2. Lowercasing everything.
    3. Stemming using Porter’s algorithm.
    4. Stopword removal.
    5. Save the result as a txt file.

### HW2: Write a program to convert a set of documents into tf-idf vectors  
    1. Construct a dictionary based on the terms extracted from the given documents  
        Record the document frequency of each term  
        Save your dictionary as a txt file (dictionary.txt)  
    2. Transfer each document into a tf-idf unit vector  
        Save it as a txt file (DocID.txt)  
    3. Write a function cosine(Docx, Docy) which loads the tf-idf vectors of documents x and y and returns their cosine similarity  

### HW3: Train Multinomial Naive Bayes
    1. Training Phase
        C <- Class 1~13
        D <- Doc 1~1095
        V <- Vocab
        N <- Doc num = 1095, Nc <- Doc in Class

        TrainMultinomialNB(C, D)
        V <- ExtractVocabulary(D)
        N <- CountDocs(D)

        for each c in C
        do 
            Nc <- CountDocsInClass(D, c)
            prior[c] <- Nc / N
            textc <- ConcatenateTextOfAllDocsInClass(D, c)

            for each t in V
            do 
                Tct <- CountTokensOfTerm(textc, t)
            for each t in V
            do 
                condprob[t][c] <- (Tct+1) / ∑(Tct’+1)

        return V, prior, condprob
        
    2. Testing Phase
        ApplyMultinomialNB(C, V, prior, condprob, d)
        W <- ExtractTokensFromDoc(V, d)
        for each c in C
        do 
            score[c] <- log prior[c]
            for each t in W
            do 
                score[c] += log condprob[t][c]

        return argmaxcscore[c]
        
##### Feature Selection (Log Likelyhood Ratio)
        SelectFeatures(D, c, k)
          V <- ExtractVocabuliary(D)
          L <- []
          for each t in V
          do
              A(t,c) <- ComputeFeatureUtility(D,t,c)
              Append(L, <t, A(t,c)>)
          return FeaturesWithLargestValues(L,k

### HW4: Hierarchical Clustering
    1. Search for the max similarity pair - <i,m>
    2. Record and merge cluster m into cluster i.
    3. Update the pair similarities between the new merged cluster i. and other clusters
    4. I[m] = 0, remove the merged cluster m.
