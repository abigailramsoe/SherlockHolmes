1. Remove unmapped reads and reads with mapping quality less than 30. You will need to use samtools view with the flag -F4 to remove unmapped reads, and the flag -q30 to remove reads with a mapping quality of under 30, e.g.  ```samtools view -b -F4 -q 30 file.sorted.bam > file.filtered.bam```
    <details> 
    <summary>Exact code</summary>
      
    ```
    samtools view -F4 -q30 sherlock.bam -b > sherlock.filtered.bam 
    samtools view -F4 -q30 holmes.bam -b > holmes.filtered.bam       
    ```
     </details>

2. How many reads were removed during filtering? 
    <details> 
    <summary>Hint</summary>

    Look at how many reads in the filtered version of your bam files, and subtract that from the number of reads in your original files (output of exercise 3, question 7).
    ```samtools view -c sherlock.filtered.bam```
     </details>
    <details> 
    <summary>Answer</summary>

    Sherlock: 477124 - 178808 = 298316
   
    Holmes: 800105 - 725729 = 74376
     </details>

4. Remove duplicate reads with samtools rmdup, e.g. ```samtools rmdup -s file.filtered.bam file.filtered.rmdup.bam```. The -s flag is very important as these are single end reads.
    <details> 
    <summary>Exact code</summary>
      
    ```
    samtools rmdup -s sherlock.filtered.bam sherlock.filtered.rmdup.bam    
    samtools rmdup -s holmes.filtered.bam holmes.filtered.rmdup.bam
    ```
     </details>


5. How many reads were duplicates?

    <details> 
    <summary>Hint</summary>
    
    This is in the rmdup output, e.g.
    [bam_rmdupse_core] X / Y = Z in library '	'
    X is the number of duplicates, Y is the total number of reads, Z is the proportion of duplicates
    </details>

    <details> 
    <summary>Answer</summary>
    
    Sherlock: 1421
   
    Holmes: 23075
    </details>


7. Get the average length of the remaining reads with ```samtools view file.filtered.rmdup.bam | awk '{print length($10)}' | datamash mean 1```

    <details> 
    <summary>Exact code</summary>
    
    ```
    samtools view sherlock.filtered.rmdup.bam | awk '{print length($10)}' | datamash mean 1
    samtools view holmes.filtered.rmdup.bam | awk '{print length($10)}' | datamash mean 1
    ```
    </details>

    <details> 
    <summary>Answer</summary>
    
    ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/19bdff6b-175e-4fb3-aa9f-8dcc4c9cb4c4)
    </details>
