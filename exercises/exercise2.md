1. Figure out how many _lines_ and how many _reads_ the FASTQ files contain. Use the command ``` zcat path/to/file/file.fastq.gz|wc -l ``` to find the number of lines and ``` zcat path/to/file/file.fastq.gz|awk '{s++}END{print s/4} ``` to find the number of reads
   
    <details> 
      <summary>Exact code: how many lines</summary>
      
      ```
      zcat SherlockHolmes/data/sherlock.fastq.gz|wc -l
      zcat SherlockHolmes/data/holmes.fastq.gz|wc -l
      ```
     </details>
     <details> 
     <summary>Exact code: how many reads</summary>
      
      ```
      zcat SherlockHolmes/data/sherlock.fastq.gz|awk '{s++}END{print s/4}'
      zcat SherlockHolmes/data/holmes.fastq.gz|awk '{s++}END{print s/4}'
      ```
      </details>
     <details> 
      <summary>Answers</summary>
      
     ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/90fe3758-01ad-4379-bc0e-0eb25dc053c9)
   
        Both Sherlock and Holmes have 3,200,000 lines, which equals 800,000 reads (divide by 4)
      </details>
    
   
3. Perform, using fastp, adapter trimming on the provided sample sequence files. Make sure to discard reads under 30 bp (-l parameter). Use it like this  ``` fastp -i path/to/file/file.fastq.gz -o file.trimmed.fastq -l 30 ```. If using the fancy code server, you must now activate the conda environment to ensure that fastp works: ``` conda activate day1 ```.
     <details> 
     <summary>Exact code</summary>
      
      ```
      fastp -i SherlockHolmes/data/sherlock.fastq.gz -o sherlock.trimmed.fastq -l 30
      fastp -i SherlockHolmes/data/holmes.fastq.gz -o holmes.trimmed.fastq -l 30
      ```
      </details>
     <details> 
      <summary>Sherlock fastp output</summary>
      
    ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/f6754801-3c96-4f2c-95f6-0071a5165761)
   
      </details>
        <details> 
      <summary>Holmes fastp output</summary>
      
    ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/73f81568-c5f2-41ba-a361-c6412a88b169)
   
      </details>   



5. What files did fastp create? Use ```ls -lort``` to have a look
    <details> 
     <summary>Answer</summary>

    ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/4b2be3a5-8ff2-4fa9-9cc4-d1db13bf3076)

      </details>

6. How many reads do the trimmed files contain?
     <details> 
     <summary>Exact code</summary>
      
      ```
      cat sherlock.trimmed.fastq|awk '{s++}END{print s/4}'
      cat holmes.trimmed.fastq.gz|awk '{s++}END{print s/4}'
      ```
      </details>
    <details> 
     <summary>Answer</summary>
      
   ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/396119d3-1c44-4709-9a04-469facf199af)

   Sherlock now has 477,112 reads and Holmes has 800,000
      </details>


8. What adapter sequences were detected?
     <details> 
       <summary>Hint</summary>
      Look at the fastp output
      </details>
    <details> 

      <summary>Answer</summary>
      Both files had the Illumina TruSeq Adapter Read1 AGATCGGAAGAGCACACGTCTGAACTCCAGTCA
      </details>

9. How many reads did not pass the filter, and why? 
     <details>  
       <summary>Hint</summary>
      Look at the fastp output
      </details>
       <details> 

      <summary>Answer</summary>
      Sherlock: 322888 reads (800000-477112) did not pass the filter, some were too low quality, some had too many Ns, and some were too short
      
      Holmes: all reads passed the filter
      </details>
      
10. What is the average read length of the trimmed reads?
     <details> 

     <summary>Code</summary>
        
      ```
    cat sherlock.trimmed.fastq | awk 'NR%4==2{sum+=length($0)}END{print sum/(NR/4)}'
    cat holmes.trimmed.fastq | awk 'NR%4==2{sum+=length($0)}END{print sum/(NR/4)}'

      ```
      </details>
      <details> 
      <summary>Answer</summary>
      Sherlock: 59.1209
      
      Holmes: 89.9716
      </details>
