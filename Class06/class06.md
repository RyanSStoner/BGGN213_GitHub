# R Functions Lab (Class 06)
Ryan Stoner (A69034955)

My first function :)

``` r
add <- function(x,y){
  x + y
}

add(1,1)
```

    [1] 2

``` r
add(c(100,1,100),1)
```

    [1] 101   2 101

Write a function to generate a random nucleotide sequences of any
length.

``` r
bases <- c("A", "C", "G", "T")

generate_DNA <- function(x){
  
  sample(bases, size=x, replace=TRUE)
}
 
generate_DNA(12)
```

     [1] "G" "G" "G" "C" "G" "G" "T" "T" "C" "C" "C" "A"

I will now repurpose this table to create proteins.

``` r
residues <- unique(bio3d::aa.table$aa1)

generate_protein <- function(x){
  
  sequence <- sample(residues, size=x, replace=TRUE)
  sequence <- paste(sequence, collapse = "")
  return(sequence)
}
 
generate_protein(12)
```

    [1] "LRTPCSPSXSNK"

Generate random protein sequences of length 6 to 12.

``` r
answer <- sapply(6:12, generate_protein)
answer
```

    [1] "ASIIFM"       "SEAEFNA"      "IYASLENH"     "DCKQHKGEW"    "GCLCMCKYWE"  
    [6] "DAFXGKQKTRC"  "LRSCEDVPFLNA"

Now to make it searchable in blast.

``` r
cat( paste(">id", 6:12, "\n", answer, sep=""), sep="\n")
```

    >id6
    ASIIFM
    >id7
    SEAEFNA
    >id8
    IYASLENH
    >id9
    DCKQHKGEW
    >id10
    GCLCMCKYWE
    >id11
    DAFXGKQKTRC
    >id12
    LRSCEDVPFLNA
