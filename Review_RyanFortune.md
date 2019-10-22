#Part 1

*I think your outputs could be better organized. Try creating subdirectories for maize, teosinte, and your graphs, and write your output files to those.
*I recommend reading the raw data from the class repository URL, so people running the code don't have to clone your whole repo:
```{r}
SNP <- read_tsv("https://raw.githubusercontent.com/EEOB-BioData/BCB546X-Fall2019/master/assignments/UNIX_Assignment/snp_position.txt")
Fang <- read_tsv("https://raw.githubusercontent.com/EEOB-BioData/BCB546X-Fall2019/master/assignments/UNIX_Assignment/fang_et_al_genotypes.txt")
```
*I wish I could help you with your decreasing for loop, but I couldn't figure it out myself and ended up doing this instead:
```{r}
filter(mMaize, Chromosome == 1) %>% write_csv(path = "Maize/MAIZE_CHR1_dec.csv")
filter(mMaize, Chromosome == 2) %>% write_csv(path = "Maize/MAIZE_CHR2_dec.csv")
filter(mMaize, Chromosome == 3) %>% write_csv(path = "Maize/MAIZE_CHR3_dec.csv")
filter(mMaize, Chromosome == 4) %>% write_csv(path = "Maize/MAIZE_CHR4_dec.csv")
filter(mMaize, Chromosome == 5) %>% write_csv(path = "Maize/MAIZE_CHR5_dec.csv")
filter(mMaize, Chromosome == 6) %>% write_csv(path = "Maize/MAIZE_CHR6_dec.csv")
filter(mMaize, Chromosome == 7) %>% write_csv(path = "Maize/MAIZE_CHR7_dec.csv")
filter(mMaize, Chromosome == 8) %>% write_csv(path = "Maize/MAIZE_CHR8_dec.csv")
filter(mMaize, Chromosome == 9) %>% write_csv(path = "Maize/MAIZE_CHR9_dec.csv")
filter(mMaize, Chromosome == 10) %>% write_csv(path = "Maize/MAIZE_CHR10_inc.csv")
```
but I think Dennis wants to see a for loop, so keep working on it!

#Part 2

*It looks like your maize and teosinte "SNPs by Chromosome" plots are exactly the same. I had the same result. I think its because all groups in the Fang dataset have the same number of columns/SNPs, which makes the two plots redundant.
*Your distribution plot of SNPs looks cool, but is a bit cluttered. Maybe also include plots with the SNP density on individual chromosomes.
*Use the ggsave() function to save your plots as output files. Currently, they only print to R.
*I couldn't figure out the heterogyzosity part either, so I can't help you there. I'm sorry :(
