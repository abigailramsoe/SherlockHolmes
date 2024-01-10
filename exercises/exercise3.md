
## Exercise 3 
1. Index the reference genome with ```bwa index``` and then the path to the reference genome. 

   <details> 
   <summary>Exact code</summary>

    ```
    bwa index SherlockHolmes/reference_genome.fasta.gz
    ```
    </details>

3. Map the trimmed fastq files with ```bwa mem```. You need to supply the reference genome, and the name of the trimmed fastq file you want to map. Redirect the output to a ".sam" file with ">", eg ```bwa mem reference.fa trimmed.fastq > file.sam```

   <details> 
   <summary>Exact code</summary>
     
    ```
    bwa mem SherlockHolmes/reference_genome.fasta.gz sherlock.trimmed.fastq > sherlock.sam 
    bwa mem SherlockHolmes/reference_genome.fasta.gz holmes.trimmed.fastq > holmes.sam
    ``` 
   </details>
   
4. Convert the sam files to bam using ```samtools view```

   <details> 
   <summary>Exact code</summary>
     
    ```
    samtools view sherlock.sam -b > sherlock.bam
    samtools view holmes.sam -b > holmes.bam
    ```
   </details>

5. Which files are bigger, the sam files or the bam files?
   <details> 
   <summary>Exact code</summary>
     
    ```
    ls -l . 
    ```
    </details>
   <details> 
    <summary>Answers</summary>
    
    ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/f3225698-e0f1-4533-986c-fa9a1c5f7e13)
 
      The sam files are bigger
    </details>

6. Visually inspect the first 10 reads of a bam file with ```samtools view file.bam|head ```, remember to use the name of one of your bam files instead of "file.bam". Are the reads ordered?
   <details> 
   <summary>Hint</summary>
   Look at the chromosomal position for each entry (each line) - it is the 4th column. If the reads are in order, this number should increase.
    </details>

7. Sort the bam files with samtools view ```samtools sort file.bam -o file.sorted.bam```.

   <details> 
   <summary>Exact code</summary>
     
    ```
    samtools sort sherlock.bam -o sherlock.sorted.bam
    samtools sort holmes.bam -o holmes.sorted.bam
    ```
    </details>
10. How many reads do the bam files contain? Use ```samtools view``` with the -c flag, e.g. ```samtools view -c file.trimmed.sorted.bam```

    <details> 
    <summary>Exact code</summary>
    
    ```
    samtools view -c sherlock.sorted.bam 
    samtools view -c holmes.sorted.bam 
    ```
    </details>   
    <details> 
    <summary>Answer</summary>
    
    ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/22dadf71-b09d-4d25-a3a3-14041f567f00)
    
    Sherlock has 477124, Holmes has 800105
    </details>   


