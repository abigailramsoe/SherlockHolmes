1. Index both of the final bam files using ```samtools index```
   
    <details> 
    <summary>Exact code</summary>
      
    ```
    samtools index sherlock.filtered.rmdup.bam 
    samtools index holmes.filtered.rmdup.bam 
    ```
     </details>

2. Run mapDamage, e.g. ```mapDamage -i file.filtered.rmdup.bam -r  reference_genome.fa --no-stats```.
    <details> 
    <summary>Exact code</summary>
      
    ```
    mapDamage -i sherlock.filtered.rmdup.bam -r  SherlockHolmes/reference_genome.fasta.gz --no-stats
    mapDamage -i holmes.filtered.rmdup.bam -r  SherlockHolmes/reference_genome.fasta.gz --no-stats
    ```
     </details>   

3. Look at the plots created using ```evince```.
    <details> 
    <summary>Exact code</summary>
      
    ```
   evince results_sherlock.filtered.rmdup/Length_plot.pdf
    ```
   </details>   
