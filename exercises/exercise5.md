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

3. Look at the plots created using ```okular```.
    <details> 
    <summary>Exact code</summary>
      
    ```
   okular results_sherlock.filtered.rmdup/Length_plot.pdf
   okular results_sherlock.filtered.rmdup/Length_plot.pdf
   okular results_holmes.filtered.rmdup/Fragmisincorporation_plot.pdf
   okular results_sherlock.filtered.rmdup/Fragmisincorporation_plot.pdf
    ```
   </details>   

    <details> 
    <summary>Plots</summary>
       
   ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/738edd02-54b1-44c9-8c54-130af1704d14)


      ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/e82dec2e-1a01-4525-ab42-d09edc1f768a)

   </details>   
