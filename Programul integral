import time

#### GENERARE TEST  START

import random

Max = 1000000
n = 10000
f = open('file.in', 'w')
f.write(str(n) + '\n')
for i in range(n):
    f.write(str(random.choice(range(Max))) + ' ')
rezultat = []

#### GENERARE TEST  END


#############################################################


#### BUBBLE SORT  START

def BS(vector_init):
    ok = False
    rezultat = [i for i in vector_init]
    while ok == False:
        ok = True
        for x in range(len(rezultat) - 1):
            if rezultat[x] > rezultat[x + 1]:
                nanu = rezultat[x]
                rezultat[x] = rezultat[x + 1]
                rezultat[x + 1] = nanu
                ok = False
    return rezultat

#### BUBBLE SORT  END


#######################################################################


#### MERGE SORT  START

def MS(vector_init):
    if len(vector_init) == 1:
        return vector_init
    st = [x for x in vector_init[:len(vector_init) // 2]]
    dr = [x for x in vector_init[len(vector_init) // 2:]]
    st = MS(st)
    dr = MS(dr)
    rezultat = []
    i = j = 0
    while i < len(st) and j < len(dr):
        if st[i] < dr[j]:
            rezultat.append(st[i])
            i += 1
        else:
            rezultat.append(dr[j])
            j += 1
    rezultat.extend(st[i:])
    rezultat.extend(dr[j:])
    return rezultat


#### MERGE SORT  END


################################################################


#### PIVOT PENTRU QS  START

def p_m_BFPRT(A):
    if len(A) <= 5:
        return sorted(A)[len(A) // 2]
    sub = [sorted(A[i:i + 5]) for i in range(0, len(A), 5)]
    med = [s[len(s) // 2] for s in sub]
    return p_m_BFPRT(med)

#### PIVOT PENTRU QS  END


################################################################


#### RADIX SORT  START

def RS(vector_init):
    vect = max(vector_init)
    vect = len(str(vect))
    p = 1
    rezultat = [x for x in vector_init]
    for i in range(vect):
        Mat = [[] for x in range(10)]
        for x in rezultat:
            Mat[x // p % 10].append(x)
        rezultat = []
        for x in Mat:
            rezultat.extend(x)
        p *= 10
    return rezultat

#### RADIX SORT  END


#################################################################


#### QUICK SORT  START

def QS(vector_init):
    if len(vector_init) == 0:
        return []
    if len(vector_init) == 1:
        return vector_init
    pivot = p_m_BFPRT(vector_init)
    st = []
    dr = []
    nanu = []

    for x in vector_init:
        if x < pivot:
            st.append(x)
        elif x == pivot:
            nanu.append(x)
        else:
            dr.append(x)
    st = QS(st)
    dr = QS(dr)
    st.extend(nanu)
    st.extend(dr)
    return st

#### QUICK SORT  END


######################################################################


#### COUNT SORT  START

def CS(vector_init):
    aparitii = [0 for x in range(max(vector_init) + 1)]
    for x in vector_init:
        aparitii[x] += 1
    rezultat = []
    for x in range(max(vector_init) + 1):
        while aparitii[x] != 0:
            rezultat.append(x)
            aparitii[x] -= 1
    return rezultat

#### COUNT SORT  END


######################################################################


NANU = [sorted, BS, MS, RS, QS, CS]

g = open("file.out", "w")


#### VERIFICARE SORTARE CORECTA/INCORECTA  START

def V (vector_init, v):
    if len(vector_init) != len(v):
        return False
    else:
        v.sort()
        for x in range(len(vector_init)):
            if vector_init[x] != v[x]:
                return False
    return True

#### VERIFICARE SORTARE CORECTA/INCORECTA  END


for nanu in NANU:                        # Realizez sortarea pentru fiecare tip in parte

    g.write("Pentru sortarea: " + str(nanu) + '\n')
    g.write('\n')

    for i in range(1, 4):             # Vreau sa compar timpul de executie al fiecarui algoritm, pentru 3 teste diferite

        f = open("file.in")
        n = f.readline().split()
        vector_init = [int(x) for x in f.readline().split()]  # Mi am creat vectorul initial
        f.close()

        timp_executie = time.time()
        vector_final = nanu(vector_init)

        g.write("Timpul de executie este de: " + str(time.time() - timp_executie) + " secunde pentru acest test ; Iar aceasta este: ")

        if V(vector_final, vector_init):
            g.write("Corecta\n")
        else:
            g.write("Incorecta\n")

    g.write('\n')


g.close()


#### Concluzii:
####   - Pe anumite teste Count Sort-ul functioneaza mai lent decat QS, RS, respectiv MS
####   - Bubble Sort-ul este cel mai lent dintre cele 5 sortari
####   - Count Sort-ul este foarte rapid pentru numere mai mici decat 10^7, complexitatea acestuia fiind O(n)
####   - Pentru numere mai mari de 10^7 este utila folosirea algoritmului QuickSort, care are o complexitate de O(nlogn)
