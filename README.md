# hse_hw1_meth

Ссылка на Colab ноутбук: https://colab.research.google.com/drive/1-5Yj5Bo_yD7irFGuugfWZ1uU2LsHZ9tI?usp=sharing

Задание 1.

Отчёт в папке html

В сравнении с секвенированием РНК (SRR3414630), можно сказать, что у BS-seq процент содержания GC почти в два раза меньше, чем у RNA-seq. На графиках видно, что цитозина в первом случае (BS) значительно меньше и гуанина тоже меньше, а тимина больше:

![бс](https://user-images.githubusercontent.com/93220053/154858096-5212b949-1ece-4926-b8d9-3ab523ae7c16.png)
![рнк](https://user-images.githubusercontent.com/93220053/154858105-df577f92-7518-4bb9-8c60-7aa6fc324a35.png)


Задание 2.

Пункт а и b.

<img width="581" alt="Безымянный" src="https://user-images.githubusercontent.com/93220053/154858696-a246c826-57fa-4d5f-a612-61c9f391c6fa.png">

Скрипт для выполнения дедупликации для всех образцов одновременно:

! ls SRR5836475_1_bismark_bt2_pe.bam SRR3824222_1_bismark_bt2_pe.bam SRR5836473_1_bismark_bt2_pe.bam | xargs -P 3 -tI{} deduplicate_bismark --bam --paired -o s_{} {}


Пункт с.

Выполнен.


Пункт d.

Отчёты в папке html

SRR5836473

![image](https://user-images.githubusercontent.com/93220053/154860037-f50495a4-3a7f-44d5-8527-0ab506473389.png)
![image](https://user-images.githubusercontent.com/93220053/154860068-82ce85b8-3404-4ef1-8743-85bea1207335.png)

SRR3824222

![image](https://user-images.githubusercontent.com/93220053/154860138-ee505939-6664-4dd8-b97b-7c0176f83d1b.png)
![image](https://user-images.githubusercontent.com/93220053/154860144-d9c9a0a7-9b01-4039-a560-83f5d34487d3.png)

SRR5836475

![image](https://user-images.githubusercontent.com/93220053/154860227-6a5c1ff0-f260-48bd-925a-a339b5ae656f.png)
![image](https://user-images.githubusercontent.com/93220053/154860232-76fa062b-1a12-4b2b-a56e-1ed8eeced444.png)

В Read 1 уровень метилирования практически постоянный, однако можно наблюдать смещение 3’-end-repair начальных позиций в двух прочтениях paired-end reads.


Пункт е.

8 Cell


import matplotlib.pyplot as plt
import pandas as pd
file_name = pd.read_csv("s_8_cell.deduplicated.bedGraph", delimiter='\t', skiprows=1, header=None)
plt.figure(figsize=[10, 5])
plt.title("Гистограмму распределения метилирования цитозинов по хромосоме 8cell", fontsize=15)
plt.xlabel("Процент метилированных цитозинов")
plt.ylabel("Частота")
plt.hist(file_name[3], bins=100, density=True)
plt.show()


![image](https://user-images.githubusercontent.com/93220053/154860791-fcf062a2-6ac3-4f18-b0db-44c0b23d063b.png)

ICM


import matplotlib.pyplot as plt
import pandas as pd
file_name = pd.read_csv("s_ICM.deduplicated.bedGraph", delimiter='\t', skiprows=1, header=None)
plt.figure(figsize=[10, 5])
plt.title("Гистограмму распределения метилирования цитозинов по хромосоме ICM", fontsize=15)
plt.xlabel("Процент метилированных цитозинов")
plt.ylabel("Частота")
plt.hist(file_name[3], bins=100, density=True)
plt.show()


![image](https://user-images.githubusercontent.com/93220053/154860838-bd14057d-44e9-488f-b9ea-de6b1511fbca.png)

Epiblast


import matplotlib.pyplot as plt
import pandas as pd
file_name = pd.read_csv("s_Epiblast.deduplicated.bedGraph", delimiter='\t', skiprows=1, header=None)
plt.figure(figsize=[10, 5])
plt.title("Гистограмму распределения метилирования цитозинов по хромосоме Epiblast", fontsize=15)
plt.xlabel("Процент метилированных цитозинов")
plt.ylabel("Частота")
plt.hist(file_name[3], bins=100, density=True)
plt.show()


![image](https://user-images.githubusercontent.com/93220053/154860885-7d4148c6-2f02-494c-be6e-0a9561a25f0f.png)

В образце 8 cell уровень метилирования средний на всём участке, в ICM уровень ниже, чем в 8cell, и резко падает. В Epiblast, уровень метилирования почти как в 8 cell.


Пункт f.

![image](https://user-images.githubusercontent.com/93220053/154861132-34986620-df12-41b6-a387-1c4ab63699b4.png)
