1. Figure out how many _lines_ and how many _reads_ the FASTQ files contain
    <details> 
      <summary>Code: how many lines</summary>
      
      ```
      zcat sherlock.fastq.gz|wc -l
      zcat holmes.fastq.gz|wc -l
      ```
     </details>
     <details> 
     <summary>Code: how many reads</summary>
      
      ```
      zcat sherlock.fastq.gz|awk '{s++}END{print s/4}'
      zcat holmes.fastq.gz|awk '{s++}END{print s/4}'
      ```
      </details>
    
   
2. Perform, using fastp, adapter trimming on the provided sample sequence files. Make sure to discard reads under 30 bp (-l parameter).
     <details> 
     <summary>Code</summary>
      
      ```
      fastp -i sherlock.fastq.gz -o sherlock.trimmed.fastq -l 30
      fastp -i holmes.fastq.gz -o holmes.trimmed.fastq -l 30
      ```
      </details>


3. What are the output files?
    <details> 
     <summary>Code</summary>
      
      ```
      ls .
      ```
      </details>

4. How many reads do the trimmed files contain?
     <details> 
     <summary>Code</summary>
      
      ```
      zcat sherlock.trimmed.fastq|awk '{s++}END{print s/4}'
      zcat holmes.trimmed.fastq.gz|awk '{s++}END{print s/4}'
      ```
      </details>

6. What adapter sequences were detected?
     <details> 
       <summary>Hint</summary>
      Look at the fastp output
      </details>

7. How many reads did not pass the filter, and why? (fastp output)
     <details>  
       <summary>Hint</summary>
      Look at the fastp output
      </details>
      
8. What is the average read length of the trimmed reads?
     <details> 

     <summary>Code</summary>
        
      ```
    cat sherlock.trimmed.fastq | awk 'NR%4==2{sum+=length($0)}END{print sum/(NR/4)}
    cat sherlock.holmes.fastq | awk 'NR%4==2{sum+=length($0)}END{print sum/(NR/4)}

      ```
      </details>
