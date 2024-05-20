# convert to lowercase
cat 'Traveller Classic Book1.txt' | tr '[:upper:]' '[:lower:]' > book1.txt
cat 'Traveller Classic Book2.txt' | tr '[:upper:]' '[:lower:]' > book2.txt
cat 'Traveller Classic Book3.txt' | tr '[:upper:]' '[:lower:]' > book3.txt

# ** remove lines with special characters, and make index file **
awk '
{
  gsub(/[^[:alpha:] ]/,"");
  for(i=1;i<=NF;i++) {
    a[$i] = a[$i] ? a[$i]", "FNR : FNR;
  }
}
END {
  for (i in a) {
    print i": "a[i];
  }
}' book1.txt | sort > book1.idx

awk '        
{
  gsub(/[^[:alpha:] ]/,"");
  for(i=1;i<=NF;i++) {
    a[$i] = a[$i] ? a[$i]", "FNR : FNR;
  }
}
END {
  for (i in a) {
    print i": "a[i];
  }
}' book2.txt | sort > book2.idx

awk '        
{
  gsub(/[^[:alpha:] ]/,"");
  for(i=1;i<=NF;i++) {
    a[$i] = a[$i] ? a[$i]", "FNR : FNR;
  }
}
END {
  for (i in a) {
    print i": "a[i];
  }
}' book3.txt | sort > book3.idx

# create pageline files from .txt files
grep -n -e "^--" Traveller\ Classic\ Book1.txt > book_pageLines.txt1
grep -n -e "^--" Traveller\ Classic\ Book2.txt > book_pageLines.txt2
grep -n -e "^--" Traveller\ Classic\ Book1.txt > book_pageLines.txt3
