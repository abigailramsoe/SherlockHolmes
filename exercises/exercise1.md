**Setup - Code Server**

If we are using the fancy code server, go to your "wdir" folder. This makes sure your data does not get deleted if you get disconnected.
```
cd course/wdir
```
<details> 
  <summary>What it should look like</summary>

  ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/f1aca610-0134-411d-97c5-0bbfc490f102)
</details>  

**Setup - Emily**

Ssh to the Emily server. Remeber to use your username instead of "abigail". Get your password from the Google Sheet - remember it doesn't appear when you type it 
```
ssh abigail@emily.popgen.dk -Y 
```
<details> 
  <summary>What it should look like</summary>

![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/2e5a3b20-5ef3-4bd1-9493-670a6d3a61e1)
</details>  

**Exercise 1**

1. Make a folder called "session2" and ```cd``` into it
   <details> 
    <summary>Exact code</summary>
       
    ```
    mkdir session2 
    cd session2
    ```
    </details>  
     <details> 
      <summary>What it should look like</summary>
         
    ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/30084564-099d-4521-9c35-e6b90aa12480)
       </details>  

    
2. First, download all the data you need by cloning this repository. This might take a few minutes. 
    ```
    git clone https://github.com/abigailramsoe/SherlockHolmes.git
    ```
    <details> 
      <summary>What it should look like</summary>
        
    ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/795ffc1a-928e-439b-9553-20a2115f1b2e)
    </details>  



3. Use the ```ls``` command to check that the folder is in your directory
    ```
    ls
    ```
    <details> 
     <summary>What it should look like</summary>
        
    ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/76a5fc47-3032-43bd-9ce7-2afafaf66bb1)
    </details>  


4. What is in the folder you just downloaded?       
      ``` 
      ls SherlockHolmes/*
      ```

   <details> 
     <summary>Answer</summary>
       
    ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/82a8d0b8-6ede-4645-aeeb-f3b90914ec35)
    </details>  


5. What are the sizes of the files in the data sub-folder?       
      ```
      du -sk SherlockHolmes/data/*
      ```
      
     <details> 
     <summary>Answer</summary>
         
    ![image](https://github.com/abigailramsoe/SherlockHolmes/assets/28560412/042d5bf0-dba1-4aa1-9bb7-001e58b04471)

   Holmes is 65,508 KB and Sherlock is 36,580 KB
    </details>  
    
