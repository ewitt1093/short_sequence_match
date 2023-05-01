# short_sequence_match
Short sequence matching

This example takes a character vector (Here named Sequences) of short sequences and matches against any BSGenome database.

```

library(EnsDb.Hsapiens.v86)
library(Biostrings)

tmp<-data.frame()
for (i in unique(Sequences)){
  print(i)
  tmp2<-vmatchPattern(i, Hsapiens) %>%data.frame()
  #uncomment this line to allow mismatches
   #tmp2<-vmatchPattern(i, Hsapiens, max.mismatch = 1) %>%data.frame()

  if(nrow(tmp2)>0){
    tmp2$Sequence = i
    print(tmp2)
  }
  # names(tmp2)<-gsub(names(tmp2), pattern = "seq", replacement = "Sequence")
  tmp<-rbind(tmp,tmp2)
}


```
