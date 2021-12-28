[[LINUX]]
# markdown

## notes
- markdown
- markup
- pandoc
- mandoc

## md to pdf
```bash
pandoc -o OUTPUTFILE.TYPE INPUTFILE.TYPE
pandoc --pdf-engine tectonic -o OUTPUTFILE.pdf INPUTFILE.md #funktioniert nicht
mandoc -T pdf INPUTFILE.md > bbq.pdf #das funxt
 
mandoc INPUTFILE.md -t ms -o OUTPUTFILE.pdf  #FUNXT 
```




