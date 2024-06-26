- 👋 Hi, I’m @sardor0506
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

import math2docx
from docx import Document
from random import shuffle

new = Document()
doc = Document('TEST.docx')


matn = doc.paragraphs

index = []
for l in range(len(matn)-1):
    if not matn[l].text.strip() :
        if not matn[l+1].text.strip() :
            index.append(l+1)
        else :
            index.append(l)



i = 0
yangi = []
while i < len(index)-1:
    yangi.append(matn[index[i]:index[i+1]])
    i+=1


nomi = input("mavzu nomi?\n>>> ")
savollar = int(input("testlar soni \n>>>"))
fayl = int(input('fayllar soni \n>>>'))
j=0

while j<fayl:
    new=Document()
    new.add_heading(f"{nomi}", 0)
    new.add_heading(f'\t\t\t\t\t{j+1}-Variant', level=1)
    shuffle(yangi)
    for i in range(savollar):
        a = new.add_paragraph(f"")
        for k in yangi[i]:
            new.add_paragraph(k.text)
            
        a.add_run(f"{i+1}-Savol")
    new.save(f"{j+1}-fayl.docx")
    j+=1



