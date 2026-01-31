touch note.txt
echo "This is a line 1" > note.txt
echo "This is a appended line" >> note.txt
echo "This is another appended line via tee" | tee -a note.txt
 head -n 2 note.txt
This is a line 1
This is a appended line
 tail -n 1 note.txt
This is another appended line via tee

