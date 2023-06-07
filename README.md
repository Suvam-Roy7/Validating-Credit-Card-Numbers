# Validating-Credit-Card-Numbers
# Can Validate One or more Credit Cards numbers in different paraments


import re

n  =  int(input("Enter Total Number of Cards : "))
a = []

for c in range(0, n):
    i = input("Card No : ")
    a.append(i)

regex = re.compile('[@_!#$%^&*()<>?/\|}{~:]')

for x in a:
    if(regex.search(x) == None):
        if(x.startswith('4') or x.startswith('5') or x.startswith('6')):
            if '-' in x:
                l1 = x.split('-')
                d1 = ''
                for c in l1:
                    d1 += c
                try:
                    d2 = int(d1)
                except : 
                    print('Invalid')
                else:
                    le = []
                    for c in l1:
                        if(len(c) == 4):
                            le.append(len(c))
                        else:
                            print('Invalid')
                            break

                    if(sum(le) == 16):
                        s = ''
                        for c in l1:
                            s += c

                        l = list(s)

                        for c in range(0, len(l)):
                            if(c == len(l)-3):
                                print('Valid')
                                break

                            else:
                                if(l[c] == l[c+1] == l[c+2] == l[c+3]):
                                    print('Invalid')
                                    break
                    elif(sum(le) > 16):
                        print('Invalid')
            else:
                l2 = x
                d1 = ''
                for c in l2:
                    d1 += c
                try:
                    d2 = int(d1)
                except : 
                    print('Invalid')
                else:
                    if(len(l2) == 16):
                        l = list(l2)
                        for c in range(0, len(l)):
                            if(c == len(l)-3):
                                print('Valid')
                                break

                            else:
                                if(l[c] == l[c+1] == l[c+2] == l[c+3] ):
                                    print('Invalid')
                                    break
                    else:
                        print('Invalid')
        else:
            print('Invalid')
    else:
        print('Invalid')
