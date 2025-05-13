***
### Descripción:
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 43522`.

### Pistas: 
```
1.- Flag is not in the usual flag format
```

### Solución:
- **Nos conectamos**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/crypto$ nc jupiter.challenges.picoctf.org 43522
-------------------------------------------------------------------------------
plcuqfit vnqn at jlbq whfu - wqndbncpj_at_p_lsnq_hfgxkf_luwgfbcqfw
-------------------------------------------------------------------------------
fhnynj wjlklqlsaipv zfqfgfrls mft ivn ivaqk tlc lw wjlklq ofshlsaipv zfqfgfrls, f hfck lmcnq mnhh zclmc ac lbq katiqapi ac vat lmc kfj, fck tiahh qngngxnqnk fglcu bt lmacu il vat uhllgj fck iqfuap knfiv, mvapv vfooncnk ivaqinnc jnfqt ful, fck mvapv a tvfhh kntpqaxn ac ait oqlonq ohfpn. wlq ivn oqntnci a mahh lchj tfj ivfi ivat hfcklmcnqwlq tl mn btnk il pfhh vag, fhivlbuv vn vfqkhj tonci f kfj lw vat hawn lc vat lmc ntifinmft f tiqfcun ijon, jni lcn oqniij wqndbncihj il xn gni maiv, f ijon fxenpi fck sapalbt fck fi ivn tfgn iagn tnctnhntt. xbi vn mft lcn lw ivltn tnctnhntt onqtlct mvl fqn snqj mnhh pfofxhn lw hllzacu fwinq ivnaq mlqhkhj fwwfaqt, fck, foofqncihj, fwinq clivacu nhtn. wjlklq ofshlsaipv, wlq actifcpn, xnufc maiv cnyi il clivacu; vat ntifin mft lw ivn tgfhhnti; vn qfc il kacn fi livnq gnc't ifxhnt, fck wftincnk lc ivng ft f ilfkj, jni fi vat knfiv ai foonfqnk ivfi vn vfk f vbckqnk ivlbtfck qlbxhnt ac vfqk pftv. fi ivn tfgn iagn, vn mft fhh vat hawn lcn lw ivn glti tnctnhntt, wfciftiapfh wnhhlmt ac ivn mvlhn katiqapi. a qnonfi, ai mft cli tiboakaijivn gfelqaij lw ivntn wfciftiapfh wnhhlmt fqn tvqnmk fck acinhhaunci nclbuvxbi ebti tnctnhnttcntt, fck f onpbhafq cfialcfh wlqg lw ai.
```
- **Nos mostrara un texto extraño.**
- **Con ayuda de una [Herramienta online](https://www.guballa.de/substitution-solver), decodificaremos dicho mensaje, y al principio de todo el texto encontraremos la bandera**
```bash
-------------------------------------------------------------------------------
congrats here is your flag - frequency_is_c_over_lambda_ogfmaunraf
-------------------------------------------------------------------------------
alexey fyodorovitch karamazov was the third son of fyodor pavlovitch karamazov, a land owner well known in our district in his own day, and still remembered among us owing to his gloomy and tragic death, which happened thirteen years ago, and which i shall describe in its proper place. for the present i will only say that this landownerfor so we used to call him, although he hardly spent a day of his life on his own estatewas a strange type, yet one pretty frequently to be met with, a type abject and vicious and at the same time senseless. but he was one of those senseless persons who are very well capable of looking after their worldly affairs, and, apparently, after nothing else. fyodor pavlovitch, for instance, began with next to nothing; his estate was of the smallest; he ran to dine at other men's tables, and fastened on them as a toady, yet at his death it appeared that he had a hundred thousand roubles in hard cash. at the same time, he was all his life one of the most senseless, fantastical fellows in the whole district. i repeat, it was not stupiditythe majority of these fantastical fellows are shrewd and intelligent enoughbut just senselessness, and a peculiar national form of it.
```

### Bandera:
```
frequency_is_c_over_lambda_ogfmaunraf
```
