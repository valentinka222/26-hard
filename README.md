# 26-hard
f = open('26_6__3ck46__3eqey (1).txt')
n = int(f.readline())
k = int(f.readline())
klienti = [list(map(int, line.split())) for line in f]
klienti.sort(key=lambda x: (x[0], -x[2]))
ans_1, ans_2 = 0, 0
perv=[[] for i in range(k)]
vtor=[[] for i in range(k)]
tret=[[] for i in range(k)]
for client in klienti:
    nach, kon, money = client
    c = False
    if money>=300:
        for kl in tret:
            if (not kl) or (nach > kl[-1][1]):
                kl.append(client)
                ans_1 += 300
                ans_2 += 1
                c = True
                break
        if c:
            continue
    if 200<=money<300 or (not c and money >= 200):
        for kl in vtor:
            if (not kl) or (nach > kl[-1][1]):
                kl.append(client)
                ans_1 += 200
                ans_2 += 1
                c = True
                break
        if c:
            continue
    if 100<=client[2]<200 or (not c and client[2] >= 100):
        for kl in perv:
            if (not kl) or (client[0] > kl[-1][1]):
                kl.append(client)
                ans_1 += 100
                ans_2 += 1
                c = True
                break

print(ans_1, ans_2)
