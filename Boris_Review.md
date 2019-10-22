### Author: Boris Alladassi
### Date: Oct 19th, 2019
### Comments and suggestions
---

Overall, good job! The work flow is well structured section by section and numbered.

I like how you provide comments for each code to describe what it does. It makes it easy to follow.

I commend how you deleted unnecessary files as you work it helps to free up some memory.

#### Suggestions

### Part I
Before transposing `fang_et_al`, you could first use function `select()` to remove columns JG_OTU and Group. Then you will not have to remove rows later. Why did you remove the row  of Sample_ID?

I would suggest you combine lines of codes together by using pipe `%>%`

It is a good habit to sort before merging although unlike UNIX, R does not require that. Section "5." could then be ignored.

**Note:** after running your for loop, a warning pops up `NAS introduced by coercions`. You could avoid this by first cropping out the **unknown** and **multiple** position.

Below is a suggestion to decompress your for loop: 

```
for (i in 1:10) {
  x_arr = filter(Teo_merge_q, Chromosome == i) %>% arrange(.,as.numeric(Position))
  write.table(x_arr, paste0('Teosinte_increasing_',i,'.txt'),sep = '\t',quote=FALSE, row.names=FALSE)
}
```
You could as well use one for loop to generate all 40 files at once.

Unless a varialbe/object name has space in it, there is no need to use back tick sings like **\`chromosome\`**.

Your for loop in section "8." is not working because your forgot the second back tick sing at the end of **Position** in the *line code 151* below:

```x_arr = arrange(x,desc(`Position))```

##### Part II

It will be nice to use option `fill= Chromosome` in the `aes()`to add color to your first plot. 

Your plot for SNP density per chromosome is not working again because of the **unknown** and **multiple** position. First filter them out. Below is a suggestion:

```ggplot(data = filter(Teo_merge_q, Position != "multiple",  Chromosome != "unknown")) + geom_density(mapping = aes(x=Position, fill=Chromosome), alpha = 0.02)```

In its current state, the plot has all the chr superimposed which makes it hard to visualize. You could use function ```facet_wrap()``` to create individual facet per chr.


You are right. It becomes easier when you first make the **fang_et_al** data ``tidy``. Then you can use `mutate` or `lapply` to make the substitutions. 

If it will help,below, is what I used to make the data tidy.

```tidy_fang <- fang %>% select(-JG_OTU) %>% 
  pivot_longer( -Sample_ID:-Group, names_to = "SNP_ID", values_to = "Sequence")```

  
##### Final notes  
-Do not forget to create an HTML or PDF file.  
-Create markdown file **README.md** that describes the content of this directory.  

